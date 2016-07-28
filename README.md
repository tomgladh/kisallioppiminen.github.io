# Kisallioppiminen.fi lähdekoodi
Täältä löydät http://kisallioppiminen.fi -sivuston lähdekoodin. Sivusto sisältää ilmaisia ja avoimia lukion pitkän matematiikan materiaaleja matematiikan oppimisen ja opettamisen tueksi. Materiaalit ovat erityisesti suunniteltu tukemaan tehostetun kisällioppimisen menetelmän käyttöä.

## Pikaohje oman version tekemiseen 
Git-versionhallintajärjestemää ja sen pohjalta tehtyä GitHub-pilvipalvelua voi käyttää monella tavalla. Tässä yksi tapa, jolla pääset nopeasti liikkeelle oman version luomisessa kisallioppiminen.fi-sivuston materiaaleista.

1. Mene osoitteeseen http://github.com
2. Luo GitHub-käyttäjätili ja tunnus täyttämällä sivun kentät ja paina nappia "Sign up for GitHub"
3. Mene sivulle https://github.com/kisallioppiminen/kisallioppiminen.github.io (jossa siis luet tätä tekstiä)
4. Paina oikeassa ylälaidassa olevaa Fork-nappia, luodaksesi oman kopion tästä lähdekoodista
5. Nyt sinut olis pitänyt uudelleenohjata omaan työtilaasi osoitteeseen `https://github.com/oma-tunnus/kisallioppiminen.github.io`, missä *oma-tunnus* on kohdassa 2 luomasi GitHub-tunnus. Paina ratasikonia "Settings".
6. Vaihda "Repository name" -kohdassa `kisallioppiminen.github.io` muotoon `oma-tunnus.github.io` ja paina "Rename"
7. Klikkaa tiedoston nimeä `_congig.yml`
8. Vaihda teksti: `url: "http://kisallioppiminen.github.io"` muotoon `url: "http://oma-tunnus.github.io"`
9. Nyt oma versio sivustostasi aukeaa osoitteessa `http://oma-tunnus.github.io`. Nyt sinun kannattaa muokata sivustoa sen verran ettei sitä sekoita alkuperäiseen kisallioppiminen.fi-sivustoon. Materiaalien lähdekoodi löytyy kansiosta `/kurssit`. 
