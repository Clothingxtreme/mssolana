Solana Drainer Installation Guide

Overview
This guide walks you through the installation process for the Solana Drainer, provided in collaboration with MS Drainer. Follow the steps below to set up your server and deploy the drainer script.

For additional details, refer to the official developer's guide here. If you have further questions, contact us on Telegram or via Email: Stupidmoni@mail.ru.

Steps to Install Solana Drainer
Step 1: Unpack the Script
Extract the provided archive to any folder on your computer.
The location doesn’t matter—choose what’s convenient.
Step 2: Rent a VPS Server
To ensure compatibility, use Ubuntu 20.04 as the operating system. You can rent a VPS from platforms like 4VPS, which supports cryptocurrency payments and requires no verification.

Create an Account on 4VPS

Visit 4VPS and log in or register for an account.
Top up your balance using cryptocurrency (e.g., 1000 RUB for optimal servers).
Rent a Server

Select a server location (avoid Russia and CIS regions).
Choose a server type (e.g., XXX-cx21 for optimal or XXX-cx01 for basic).
Set the OS to Ubuntu 20.04 (don’t select any pre-installed recipes).
Access Server Details

After server activation, copy the IP address, username (root), and password from the server control panel.
Step 3: Prepare the Server
On your Windows PC, open PowerShell as an administrator.

Connect to the server using:

ssh root@SERVER_IP
Replace SERVER_IP with the server's actual IP address.

Enter the server password when prompted.

Step 4: Install Dependencies
Run the following commands on the server one by one:

sudo apt-get update && sudo apt-get upgrade  
sudo apt install curl  
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash  
source ~/.bashrc  
nvm install --lts  
node -v && npm -v  
Ensure that the versions of Node.js and npm are displayed after running the final command.

Step 5: Upload Files to the Server
Download and install FileZilla here.

Connect to the server using:

Host: sftp://SERVER_IP
Username: root
Password: Server password.
Navigate to /root and create a folder named builder.

Upload all files from the unpacked drainer archive to the builder directory.

Step 6: Configure Files
Edit the following files to match your setup:

database.json: Update fields like telegramBotToken, ownerPublicKey, and connectionKey.

config.php: Add server-specific details such as $BACKEND_HOST (e.g., SERVER_IP:80) and $GROUP_CHAT_ID.

settings.json: Customize drainer behavior (e.g., wallet settings, fake profit values).

main.js: Replace "RPC LINK" with the Solana HTTPS RPC URL.

Upload the updated files back to the server.

Step 7: Build and Run
Return to PowerShell and run:

cd /root/builder/frontend  
npm install  
npm run build  
If errors occur, use these commands:

npm run fix  
npm run build  
Start the backend:

cd /root/builder  
npm i pm2 -g  
npm install  
pm2 start index.js --watch index.js  
pm2 save && pm2 list  
Step 8: Deploy the Website
Purchase a domain and hosting service (e.g., via 4HOST or 4DOMAINS).
Upload the prepared files from the frontend/dist folder to the hosting’s root directory.
Ensure PHP 8 or higher is enabled on your hosting.
Support
For assistance, reach out via Telegram or email Stupidmoni@mail.ru.

Only dm if you are serious
Because I wouldn't entertain time waster or should I say those that love to waste my time by asking for free or pricing stupid amount please stay away.
