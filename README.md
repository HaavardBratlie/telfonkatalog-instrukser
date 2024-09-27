# Telefonkatalog på raspberry Pi

1. ## Nedlastinger
Last ned raspberry pi imager og ubuntu på en annen maskin.                                        
    Pi Imager: https://www.raspberrypi.com/software/    
    Bla ned på nettsiden til der det står "Download for Windows" og download

    Ubuntu: https://ubuntu.com/download/raspberry-pi
    Bla ned på nettsiden til der det står "Ubuntu 24.04.1 LTS" og trykk på den grønne knappen "Download Ubuntu Desktop 24.04.1 LTS".

 Gjennomfør raspberry pi imager installer. Trykk install og vent til den er ferdig. da burde imager komme opp automatisk.
2. ## pi imager
Inne på Imager skal du velge vilker variant av pi du har, hvilket opperativ system og hvor du skal laste ned.  
    Under "Raspberry pi Device" velger du den varianten du har, jeg har raspberry pi 4.       
        Under "Operating System" blar du ned til "Use custom" og velg Ubuntu filen du lasted ned    
            Under storage skal du velge hvilket minnekort du skal laste ned på. Put in minnekortet i pcen og velg det.
3. ## Pi setup
Trykk "Next" og så trykk på "Edit Settings". her kan du endre hostname, username, passord og språk på keyboard. jeg ambefaler og sette et bra username og passord men alt trengs ikke.                                          
Øverst ser du tre overskrifter, trykk på "Services". her skal du kjekke av boksen "enable ssh" også "use password authentication".
Trykk på save og så YES. hvis du allerede har noe innstalert på minnekortet vil det spørre deg om du vil fjerne alt før du downloader. trykk YES.
Når downloaden er ferdig tar du ut minnekortet å putter den in i pien.
fullfør system configuration.

4. ## terminal 
CTRL + ALT + T for å åpne terminalen.    
Skriv: 
```console
sudo apt update
```
vent til den er ferdig, så skriv:
```console
sudo apt upgrade
```
den spør Y/N. skriv Y


5. ## installer firewall og ssh
skriv
```console
sudo apt install ufw
```
dette installerer firewall
så skriv:
```console
sudo ufw enable
```
dette aktiverer firewall ved oppstart.
for å aktivere ssh skriv:
```console
sudo ufw allow ssh
```

6. ## bruk ssh
installer ssh med:
```console
sudo apt install openssh-server 
```
enable ssh med:
```console
sudo systemctl enable ssh 
```
start ssh med:
```console
sudo systemctl start ssh 
```

7. ## Finn ip adresse for ssh
```console
ip a
```

8. ## Programmer du trenger på PI
python
```
sudo apt install python3-pip
```
git
```
sudo apt install git
```
mariaDB
```
sudo apt install mariadb-server
```
mySQL
```
sudo mysql_secure_installation
```

9. ## Lag en bruker på mariaDB
for å gå inn på mariaDB
```
sudo mariadb –u root
```
Lag ny bruker med:
```
CREATE USER 'dittusername'@'localhost' IDENTIFIED BY 'dittpassword';
```
Du må gi rettigheter til brukeren:
```
GRANT ALL PRIVILEGES ON *.* TO 'username'@’localhost’ IDENTIFIED BY 'password';
```

Så må du oppdatere rettighetene:
```
FLUSH PRIVILEGES;
```