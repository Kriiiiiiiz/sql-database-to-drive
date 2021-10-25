# Auto backup sql databases to Google Drive
A script to safely and automatically backup and upload your sql databases to Google Drive.
You can backup databases running on localhost but also you'll be able to backup external databses you have access to.

Feel free to text me on my [Discord](https://discord.io/KrizOnDev) if you need help !

## 🔩 Dependencies
* [labbots / google-drive-upload](https://github.com/labbots/google-drive-upload#documentation) (Required) This will handle .sql files uploads to Google Drive.
* Postfix (Optional) Only if you want to receive crontab's e-mail notifications when a backup it's created and uploaded.


## 🔧 How to Install
Keep in mind that if you want to back up more than one database you'll need to set up one script per database.

1. Lets download the script to your /home directory
```bash
wget -L https://github.com/Kriiiiiiiz/sql-database-to-drive/releases/latest/download/db_backup.sh -P /home/
```
2. Open it with your favorite text editor, i'll suggest nano
```bash
nano /home/db_bakckup.sh
```
3. Check lines from 3 to 16 and fill with the required credentials, when finished save the file.
4. Set the correct permissions
```bash
sudo chmod +x /home/db_bakckup.sh
```


## ⚙️⏰ Automatize
We'll use crontab to automatize database backup and upload to Google Drive, as said you will need one script per database so the same for crons, if you want to auto backup and upload 3 databases you'll need 3 scripts, each one configured separatedly and with different names, as well 3 cronjobs.

1. Run
```bash
sudo crontab -e
```
2. Once opened, at the end of the file, paste the line below
```bash
0 0 * * * sh /home/db_backup.sh 

#This example cron will create and upload a backup of the database specified in
#the script everyday at 12:00 at the end of the day. Change it to your needs.
```

## 🔔 Notifications
Optionally you can add an e-mail adress to your crontab to be able to get notified when backups and uploads are done and know if everything worked fine, just add the line below to your crontab.

1. Run
```bash
sudo apt-get install postfix

#Follow the steps to finish postifix's installation.
```
2. Then add the line below to your crontab with your e-mail adress
```bash
MAILTO=name@domain.com
```
