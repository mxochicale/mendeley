# I am not using [Mendeley](https://www.mendeley.com/) since 2017
These are the reasons:
* The migration from machine to machine might be time consuming, specially
if you don't know anything about sqlite3.
* If you naively synchronise your local database with the online database,
you will have, at some point, a notification about a payment wall and if you want to
continue using the service which is a valid and understandable business model
but I like projects that have few or no barriers.
* I dislike that idea that all my references and annotations of my research
interests are part of mendelay's databases. I believe that such references an
annotations, maybe only meaningful for me, should be available for anyone, anywhere.
* Mendeley is neither free software nor open source and this is the first point of
more reasons to [move away from mendeley](https://github.com/rdiaz02/Adios_Mendeley#why-move-away-from-mendeley)

# Looking for alternatives for mendelay
* [Zotero](https://github.com/flinz/mendeley2zotero)
* I am very interested in using GitHub as a replacement of Mendelay and Zotero
using the issue system as in [arXivTimes](https://github.com/arXivTimes/arXivTimes/issues).
I personally like the idea of adding tags and any extra information in the issues.

# Outdated files


## a_get_lastest_mendeley.sh
  1. check the lastest version https://www.mendeley.com/release-notes/development/
  2. update mendeley_latest_version (Line 27)
  3. update lines to be commented "sed -i '10,11 s/^/#/' mendeley_launcher.desktop"
  4. run the current script


## disable synchronize attached files
  Go to Synchronization options to disable Synchronize attached files

## Migrate from one computer to another

** How can I migrate my data from one PC to another?
Advanced users can also migrate by copying their database file from one machine to another.
First log in to both machines with the same account details and then copy your database file
across from the Mendeley data folder on the first machine to the Mendeley data folder
on the second.
[http://support.mendeley.com/customer/en/portal/articles/227942-how-can-i-migrate-my-data-from-one-pc-to-another-]


** Additional note:

To locate your Mendeley  Desktop database automatically, please open Mendeley Desktop
and press Ctrl + Shift + D on your keyboard before clicking Open Data Directory
to locate your data directory on your hard drive.

You can also find your database manually.
In order to locate yours, open an explorer/finder window and navigate to:
Linux: ~/.local/share/data/Mendeley Ltd./Mendeley Desktop/

If you have not entered an e-mail address into Mendeley Desktop, your database file is called
"online.sqlite". If you have entered your email address, the local database is a file called
"«yourEmailAddress»@www.mendeley.com.sqlite"; for example,
"john.doe@provider.com@www.mendeley.com.sqlite".
The database file containing information on the selected watched folder settings is
called "monitor.sqlite".

[http://support.mendeley.com/customer/portal/articles/227951-how-do-i-locate-mendeley-desktop-database-files-on-my-computer-]


The database is stored in SQLite format.
You can browse its contents using the SQLiteBrowser tool
(http://sourceforge.net/projects/sqlitebrowser/) amongst others.

Install SQLite Database Browser in Ubuntu

$ sudo apt-get install sqlitebrowser


## how to modify Mendeley’s database manually?



```
Arun Viswanathan aka n30bli7z said...

    @Paul

    Mendeley stores the full file paths to your files in its database. It is possible that the file paths in the database are pointing to the old location.

    Can you do the following (this wont change anything on the system):

    1. Open a terminal.
    2. Install sqlite (if you dont have it) using
    sudo apt-get install sqlite3
    3. Go to the mendeley database directory
    4. You will find your database file stored as your @www.mendeley.com.sqlite
    5. sqlite3 @www.mendeley.com.sqlite
    6. select * from Files;

    This should list the full paths of all your files. Are they pointing to their new location? Or are they showing the old path?

http://n30bli7z.blogspot.co.uk/2009/10/using-mendeley-effectivey-on-multiple.html
```



```
db="perez.xochicale@gmail.com@www.mendeley.com.sqlite"
sqlite3 $db  "update Files set localUrl = replace(localUrl, '/map479-admin/', '/map479/');"

```

## Advices



This already works for me in OneDrive.

I have my stored PDFs in a OneDrive folder that I called Mendeley. In the file
organizer tab under Tools/Options, I refer the location as
C:\Users\[xxx]\OneDrive\Mendeley (in which [xxx] is my different username for each
  computer where I have this set-up). Furthermore I ensure that the way Mendeley
  renames the files are always the same on each computer (i.e. checked
    "rename document files" and renames the Author Year Title "Hyphen-separated"
    (order and style must be the same everywhere too, of course)).
    This set-up works like a charm on all my devices (I have mendeley and OneDrive
      installed on my Win7 lab computer, my Win8.1 home desktop and my Win10 laptop).

I do have to say that in the beginning (I had this set-up on my home desk first,
  added the laptop a few months later) Mendeley tried to download some of the
  PDFs into the OneDrive folder (and added a (1) behind the file name).
  I think this is because OneDrive had not yet synced the folder on the laptop.
  This was a one time issue though. I stopped Mendeley, waited until all the
  files in OneDrive were synced, restarted Mendeley, waited until everything
  was synced in mendeley, then cleaned up the folder using "Tidy Up"
  (Tools/Options/File Organizer) --> Archive unused files --> delete Archived files.
  I now always wait until OneDrive synced everything onto whatever computer
  I am using and only after that I open Mendeley. No sync issues after that anymore.

Double check your "rename" settings and if they are identical, perhaps it is a Drive/Dropbox issue rather than a Mendeley one.
[Source](https://feedback.mendeley.com/forums/4941-general/suggestions/11024835-to-integrate-mendeley-with-google-drive-and-dropbo)


## TODO:
In case that someone wants to use medeley, these are some of my pending points
when I was actively using medeley ( 2014 and 2015)
- [ ] migrate library to another computer as an example
- [ ] change the version of the OS and architecture
- [ ] document the following files b_replace_libary.sh, c_get_mendeley_database.sh,
  mendeley_launcher.desktop, perez.xochicale@gmail.com@www.mendeley.com.sqlite
