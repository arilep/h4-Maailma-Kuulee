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

## Tehtävä-A

## Tehtävä-B

## Tehtävä-C

## Tehtävä-D
