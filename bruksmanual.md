# Hvordan sette opp Raspberry Pi og Ubuntu Server

## Forhåndsinformasjon
1. Denne bruksmanualen viser hvordan man setter opp programvare på en Raspberry Pi, ikke hvordan man setter den opp fysisk.
2. Manualen bruker hovedsakelig Google Chrome som søkemotor.
3. Raspberry Pi 4B brukes som eksempel.
4. Det forutsettes at du kan bruke en søkemotor og laste ned filer fra internett.

## Sette opp Raspberry Pi
1. Gå til en søkemotoren og søk etter **"Raspberry Pi Imager"** eller bruk [denne linken](https://www.raspberrypi.com/software/).
2. Klikk på lenken, og bla ned til **Install Raspberry Pi OS using Raspberry Pi Imager**. Klikk der. (Referer til Bilde 1)
3. Når du har gjort dette, vil du se et skjermbilde som viser installasjonsveiledning for Raspberry Pi OS. (Referer til Bilde 2)
Hvis du gjorde alt riktig, så kommer du til å se dette (Referer til Bilde 3)
4. Trykk på **Install**.
5. Når installasjonen er ferdig, aktiver **Run Raspberry Pi Imager** og trykk **Finish**. (Referer til Bilde 4)
Hvis du har fult trinnene riktig, så har du kommet til denne skjermen (Referer til Bilde 5)
6. 6.	Velg din «Raspberry Pi Device», «Operating System», og «Storage». I dette eksempel så kommer jeg til å velge «Raspberry Pi 4», «Ubuntu Desktop», og «SD Disk Device» (Referer til Bilde 6). 
7. Klikk **Next**, og deretter **Yes** hvis en bekreftelsesdialog vises. (Referer til Bilde 7)
8. Etter at du har lastet opp operativsystemet på SD-kortet, ta ut kortet fra PC-en din og sett det inn i din Raspberry Pi.
9. Koble Raspberry Pi til en skjerm og følg oppsettinstruksjonene.

Nå har du satt opp din programvare i din raspberry pi.

## Sette opp Ubuntu Server
1. Åpne terminalen på Raspberry Pi-en din etter oppstart av Ubuntu.
2. Følg disse kommandoene for å sette opp SSH:
   - **Oppdatering av programvare:**
     ```bash
     sudo apt update 
     sudo apt upgrade
     ```
   - **Sett opp brannmur med UFW:**
     ```bash
     sudo apt install ufw
     sudo ufw enable
     sudo ufw allow ssh
     sudo ufw status
     ```
   - **Installer SSH-server:**
     ```bash
     sudo apt install openssh-server
     sudo systemctl enable ssh
     sudo systemctl start ssh
     ```
   - **Finn IP-adressen din:**
     ```bash
     ip a
     ```
     IP-adressen vises ved **eth0** for kablet nettverk eller **wlan0** for trådløst nettverk.

3. Installer nødvendige pakker:
   - **Installer Git, Python og MariaDB:**
     ```bash
     sudo apt install python3-pip 
     sudo apt install git 
     sudo apt install mariadb-server
     sudo mysql_secure_installation
     ```
   - **Lag en ny databasebruker:**
     ```bash
     sudo mariadb -u root
     
     CREATE USER 'brukernavn'@'localhost' IDENTIFIED BY 'passord';

     GRANT ALL PRIVILEGES ON *.* TO 'brukernavn'@'localhost';

     FLUSH PRIVILEGES;

     EXIT;
     ```

4. Koble til Raspberry Pi fra en annen enhet via SSH:
   ```bash
   ssh brukernavn@ip
  Nå kan du bruke ubuntu fra Pcen.