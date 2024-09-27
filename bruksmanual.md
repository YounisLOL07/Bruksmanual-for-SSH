# Hvordan sette opp Raspberry Pi og Ubuntu Server

## Forhåndsinformasjon
1. Denne bruksmanualen viser hvordan man setter opp programvare på en Raspberry Pi, ikke hvordan man setter den opp fysisk.
2. Manualen bruker hovedsakelig Google Chrome som søkemotor.
3. Raspberry Pi 4B brukes som eksempel.
4. Det forutsettes at du kan bruke en søkemotor og laste ned filer fra internett.

## Sette opp Raspberry Pi
1. Gå til en søkemotor og søk etter **"Raspberry Pi Imager"** eller bruk [denne linken](https://www.raspberrypi.com/software/).
2. Klikk på lenken, og bla ned til **Install Raspberry Pi OS using Raspberry Pi Imager**. Klikk der.
3. Når du har gjort dette, vil du se et skjermbilde som viser installasjonsveiledning for Raspberry Pi OS.
4. Trykk på **Install**.
5. Når installasjonen er ferdig, aktiver **Run Raspberry Pi Imager** og trykk **Finish**.
6. Velg din Raspberry Pi-enhet, operativsystem (f.eks. Ubuntu Desktop), og lagringsenhet (f.eks. SD-kort).
7. Klikk **Next**, og deretter **Yes** hvis en bekreftelsesdialog vises.
8. Etter at du har lastet opp operativsystemet på SD-kortet, ta ut kortet fra PC-en din og sett det inn i din Raspberry Pi.
9. Koble Raspberry Pi til en skjerm og følg oppsettinstruksjonene.

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
