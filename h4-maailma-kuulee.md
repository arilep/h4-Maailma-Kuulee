## Tehtävissä käytetty ympäristö

- Käyttöjärjestelmä: Windows 11 Home 64-bit
- Suoritin: AMD Ryzen 7 5800X 8-Core Processor
- Muisti: 32GB RAM
- Näytönohjain: NVIDIA GeForce RTX 3080
- Virtualisointiohjelmisto: Oracle VM VirtualBox 7.0

- Internet yhteys: DNA Netti 400M (Download 400Mbps / Upload 200Mbps)

## Tehtävä-X
### Pilvipalvelimen vuokraus ja asennus

- Vapaaehtoinen, mutta suositeltava: Muista hyödyntää GitHub Education paketti (GitHub Student Developer Pack)
- --> Palvelin ja domainnimi ilmaiseksi käyttöön kurssin ajan.
- Sopivia virtuaalipalvelinten vuokraajia löytyy paljon, mm. Linode, DigitalOcean ja UpCloud.
- Valitse sopivin ja rekisteröidy käyttäjäksi.
- Rekisteröinnin ja maksutietojen jälkeen muistettavaa:
    - Käyttöjärjestelmäksi kannattaa valita Debianin uusin versio
    - Virtuaalikoneen paketiksi kannattaa alkuun valita mahdollisimman edullinen peruspaketti, resurssien määrää on mahdollista kasvattaa myöhemmin.
    - Datakeskus kannattaa valita EU:n sisältä, jottei ongelmia tule esimerkiksi GDPR:n kanssa.
    - Salasanan merkitys tietoturvassa on äärimmäisen tärkeä. Autentikointimenetelmistä SSH-avaimet on turvallisin.
    - Mitään ylimääräisiä lisäpalveluita ei tässä kohtaa ole vielä tarvetta hankkia.

### Palvelin suojaan palomuurilla

- Terminaalissa yhteys virtuaalipalvelimeen: $ ssh root@'ip-osoite'
- Palomuurin asennus: $ sudo apt-get install ufw
- Palomuuriin reikä porttia varten: $ sudo ufw allow 22/tcp
- Palomuuri päälle: $ sudo ufw enable

### Kotisivut palvelimelle

- Käyttäjän luominen virtuaalipalvelimen terminaalissa: $ sudo adduser 'username'
- Käyttäjästä pääkäyttäjä: $ sudo adduser 'username' sudo
- Uuden käyttäjän tunnusten testaus, otetaan yhteys: $ ssh 'username'@'ip-osoite'
- Juuren 'root' lukitseminen: $ sudo usermod -lock root
- Reikä palomuuriin uutta porttia varten: $ sudo ufw allow 80/tcp

### Palvelimen ohjelmien päivitys

- SSH-yhteys virtuaalipalvelimeen pääkäyttäjänä, jonka jälkeen ajetaan komennot:
  - $ sudo apt-get update
  - $ sudo apt-get upgrade
  - $ sudo apt-get dist-upgrade

## Tehtävä-A - Vuokraa oma virtuaalipalvelin haluamaltasi palveluntarjoajalta.

Päätin valita palveluntarjoajaksi UpCloudin, joka on itselleni edes hieman tuttu.

![image](https://github.com/user-attachments/assets/e18ad7d6-f74b-442a-b349-4ce40002ad77)

--> Signup painikkeesta siirryin rekisteröitymään

![image](https://github.com/user-attachments/assets/cc42683a-295d-43db-8f73-2dedf83098c4)

--> Syötin tiedot ja vahvistin sähköpostiosoitteeni.

--> Tämän jälkeen loin käyttäjätunnukseni ja määritin salasanan. Tämän jälkeen sain ilmoituksen että käyttäjätunnuksen luominen onnistui.

--> Seuraavaksi syötin maksukorttini tiedot.

![image](https://github.com/user-attachments/assets/5c310c1f-4771-4fc9-acec-36b42c65200d)

Seuraavaksi siirryin eteenpäin kohdasta 'Deploy now' -> 'Server'.

Valitsin datakeskukseksi FI-HEL 1

![image](https://github.com/user-attachments/assets/3d9fc55b-6098-4db9-8c7e-76facfd9cc1b)

Plan -kohdasta edullisin perusvaihtoehto:
![image](https://github.com/user-attachments/assets/a1d676eb-a241-4454-8762-9d56937bd44a)

Storage: ei valintoja

Automated backups: ei valintoja

Operating system: Viimeisin Debian versio
![image](https://github.com/user-attachments/assets/60d5e730-111b-4001-9e76-392d1cb01399)

Network ikkunassa jatkoin oletusasetuksilla
![image](https://github.com/user-attachments/assets/3a5b8440-6daf-4f1f-aca8-9a8b8bc2e5d9)

Optionals: ei valintoja

Tarvitsin SSH-avaimen seuraavaa kohtaa varten. Asensin OpenSSH-työkalun:
![image](https://github.com/user-attachments/assets/b3987b5e-18c4-41c3-8d8a-a876240736d0)

Seuraavaksi loin SSH avaimen ```ssh-keygen``` -komennolla ja hain julkisen SSH-avaimeni ja kopioin sen (ctrl+shift+c) 
![image](https://github.com/user-attachments/assets/c0373efe-9f41-46ae-ab89-19ce4c8ba833)

SSH-avain otettu käyttöön:
![image](https://github.com/user-attachments/assets/0fb8cb3b-2a14-4611-9d88-14eb324662d1)

Initialization script: ei valintoja

Server Configuration: ei valintoja

Lopuksi 'Deploy'

Palvelin käytössä:
![image](https://github.com/user-attachments/assets/eb55a832-bc4b-4886-b7d5-04015ecbb915)

## Tehtävä-B - Alkutoimet virtuaalipalvelimella

Seuraavaksi otin terminaalista yhteyden komennolla ```ssh root@94.237.114.12``` ja asensin palomuurin komennolla ```sudo apt-get install ufw```

![image](https://github.com/user-attachments/assets/bf2ab3e9-5b29-494c-8a97-734d83b0a21b)

Seuraavaksi tein reiät SSH:ta ja HTTP-liikennettä varten portteihin komennolla ```sudo ufw allow 22/tcp``` ```sudo ufw allow 80/tcp``` ja otin palomuurin käyttöön komennolla ```sudo ufw enable```
(huom. allow 80/tcp jäi vahingossa kuvakaappauksesta pois).

![image](https://github.com/user-attachments/assets/1e54d86e-c03d-4eee-914d-c882223e1506)

Tämän jälkeen loin uuden käyttäjän 'ap'

```$ sudo adduser ap```
```$ sudo adduser ap sudo```

Tämän jälkeen kopioin Root:n SSH-asetukset, jotta kirjautuminen onnistui uudella käyttäjällä.

```sudo cp -rvn /root/.ssh/ /home/jurpo/``` <-- kopiointi

```sudo chown -R ap:ap /home/jurpo/``` <-- oikeudet hakemistoihin uudella käyttäjällä

![image](https://github.com/user-attachments/assets/7a5e2b4b-3f0d-447d-a27c-bd3104bb8da2)

Suljetaan root-tunnus

```sudo usermod --lock root```

![image](https://github.com/user-attachments/assets/7b7425ab-6e2b-4448-89e4-1165d0597cd4)

```sudo mv -nv /root/.ssh/ /root/DISABLED-ssh/```

![image](https://github.com/user-attachments/assets/7b5edf2d-037e-4006-a2aa-356b62175010)

Ja ajetaan päivitykset + paketteja helpottamaan palvelimen hallintaa:

![image](https://github.com/user-attachments/assets/78613062-0b0f-4a83-8d63-9959aa73d31e)

![image](https://github.com/user-attachments/assets/9a59b9b4-ea6d-42d2-95a4-d5bda0fff513)



## Tehtävä-C - Weppipalvelimen asennus virtuaalipalvelimelle

Aloitetaan asentamalla Apache2:

![image](https://github.com/user-attachments/assets/ed6bbc42-fe83-4d9d-bb45-54b3bdec1e73)

Ajoin komennon ```echo "Default"|sudo tee /var/www/html.index.html``` (luotiin hakemisto ja korvattiin sisältö)

![image](https://github.com/user-attachments/assets/e5e9e0d9-a318-4851-91bb-d99e36d35cb8)

![image](https://github.com/user-attachments/assets/04efce9b-915d-4291-a7c9-b0a3924eeb7a)

Sivu selaimessa:

![image](https://github.com/user-attachments/assets/1a9df973-1bc7-4646-8f74-e0a0f0d786ec)

## Tehtävä-D

### Luodaan uusi Name-based Virtual Host

```sudoedit /etc/apache2/sites-available/munsivu.example.com.conf```

![image](https://github.com/user-attachments/assets/e1e70443-04f7-4e52-b31d-bb0c8fe05114)

Lisätty sisältö:

![image](https://github.com/user-attachments/assets/c64cedfd-a5b5-4018-b38e-5ffad493d507)

Enable site:

![image](https://github.com/user-attachments/assets/2b57efb2-9185-496b-906c-1c9075dda5e0)

Restart Apache:

![image](https://github.com/user-attachments/assets/05c3b5fd-8ad6-4de8-9ead-7421d2e36c35)

Luodaan sivu:

![image](https://github.com/user-attachments/assets/b6bec95b-83a6-4ae1-9295-3e70593fb9f6)

Kun yritin avata sivuston, sain vihrheen 403. Ongelma oli tiedostojen käyttöoikeuksissa (verkkopalvelimella ei ollut pääsyä kotihakemistoni resursseihin).

Sain ratkaistua tämän ajamalla alla olevan komennon, jolla annetaan luku- ja suoritusoikeudet (read & execute).

```bash
sudo chmod 755 /home/ap
```
Ja sitten lähti pelittämään:

![image](https://github.com/user-attachments/assets/c4e57c34-59e8-4002-bb77-c8733cdefa7e)

