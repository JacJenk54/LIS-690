# Managing Software

## Notes
- `sudo` = execute a command as another user
  - Allows users to safely edit a software system without using the superuser's "root" account
- `groups` = tell the user what group they belong to
- `sudo apt update` = tells user if there is an update avilable
- `sudo apt upgrade` = update software
- `apt search` = search for a package name
- `apt show`: shows more information about a package
- `sudo apt install` = install a package
- `sudo apt --purge remove` = remove a package and its system configuration files
- `sudo apt autoremove` = remove dependencies software
  - Removing dependencies helps keep a system clean
- `sudo apt clean` = remove files that were intalled with a package

## Screenshots
`sudo apt update`
<img width="1440" alt="Screenshot 2024-02-24 at 12 58 40 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/771f41cf-5947-48e8-94ca-ab2d2f0fb661">

`sudo apt upgrade`
<img width="1440" alt="Screenshot 2024-02-24 at 12 59 03 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/6e8d77ea-3cf4-44b7-b043-91153ca94231">

`apt search`
<img width="1440" alt="Screenshot 2024-02-24 at 1 25 05 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/1f393eff-3df9-4121-be58-d2fc7295e155">

`apt show`
<img width="1440" alt="Screenshot 2024-02-24 at 1 25 23 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/ac455776-380b-47b7-92f2-fc41aeb31801">

`sudo apt install`
<img width="1440" alt="Screenshot 2024-02-24 at 1 26 53 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/27ce16f7-a9fb-41b1-aa51-3420ab68b8cd">

`sudo apt --purge remove`
<img width="1440" alt="Screenshot 2024-02-24 at 1 28 05 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/bbb4c7fb-34c5-43b7-b19f-8c9728d8beb5">

# Library Search

## Installing Yaz
1. Search for `yaz`: `apt search yaz`
2. Show the information for `yaz`: `apt show yaz`
3. Instal `yaz`: `sudo apt install yaz`

## Using Yaz
1. Open `yaz`: yaz-client
2. Connect to a library's OPAC/discovery service: `open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY`
3. Find informations: `find`

## Screenshots
Searchig for `yaz`
<img width="1440" alt="Screenshot 2024-02-24 at 1 57 24 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/6c8992c2-1d7f-4ac5-ace1-99348a9a4a20">
Viewing `yaz`
<img width="1440" alt="Screenshot 2024-02-24 at 1 57 03 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/f7f4733e-efc5-4aab-87c6-b49dcd6fdd4d">
Installing `yaz`
<img width="1440" alt="Screenshot 2024-02-24 at 1 57 12 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/f946306d-bf37-4ed4-9fa4-ffbadfa6d128">
Connecting to UK
<img width="1440" alt="Screenshot 2024-02-24 at 2 00 22 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/df8642eb-55fe-4148-ac23-8dfede25e7c2">
