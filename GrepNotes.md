# Grep Notes

### Simple Commands
- `grep` = search text
- `-i` = ignore case
- `-v` = inverse search
- `c` = count
- `w` = whole words
- `^` = start of a line
- `$` = end of a line

### Scopus Articles
<img width="1440" alt="Scopus" src="https://github.com/JacJenk54/LIS-690/assets/157763172/75cd554b-9d2b-4371-8a30-895e718168ec">

### Document Types
`grep "^@" scopus.bib`
<img width="1440" alt="Screenshot 2024-02-23 at 4 27 38 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/2b51b1fd-b894-4d17-bbbc-b76ed96fc54e">

### Journal Titles
`grep "journal" scopus.bib`
<img width="1440" alt="Screenshot 2024-02-23 at 4 28 08 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/e813220f-8b1b-40f5-82fa-99f51b18a2bf">

`grep "journal =" scopus.bib | cut -d"=" -f2 | \
    sed 's/ {//' | sed 's/},//' | \
    sort | uniq -c | sort`
<img width="1440" alt="Screenshot 2024-02-23 at 4 34 43 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/241f7aff-8983-46b6-a035-df452efde46d">

### Citations
` grep -o "Cited by: [0-9]*" scopus.bib | \
    awk -F":" \
    'BEGIN { printf "Total Citations: "} \
    { sum += $2; } \
    END { print sum }'`
<img width="1440" alt="Screenshot 2024-02-23 at 4 31 09 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/3486c759-ac84-4e19-b810-7d3f1471da07">
