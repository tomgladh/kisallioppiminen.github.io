---
title: Ohjelmointi &ndash; 2015
layout: course
main-class: has-aside
sidenav: 2015/ohjelmointi
---

\section{Lineaariset yhtälöryhmät}

%Lisää tähän lukuun:
%Miksi käyttää Gaussin-Jordanin -menetelmää, kun yhtälöryhmiä voi ratkaista muutenkin?
%Kuinka ratkaisujen lukumäärän näkee porrasmatriisista.

\emph{Lineaarinen yhtälöryhmä} on yhtälöryhmä, joka on muotoa
\begin{equation*}
\left\{
\begin{array}{rcrcccrcr}
a_{11}x_1&+&a_{12}x_2&+&\cdots&+&a_{1n}x_n&=&b_1 \\
a_{21}x_1&+&a_{22}x_2&+&\cdots&+&a_{2n}x_n&=&b_2 \\
&&&&&&&\vdots & \\
a_{m1}x_1&+&a_{m2}x_2&+&\cdots&+&a_{mn}x_n&=&b_m \\
\end{array}
\right.
\end{equation*}
missä $a_{11},\dots,a_{mn},b_1,\dots,b_m \in \R$.
Symbolit $x_1,x_2,\dots,x_n$ ovat yhtälöiden tuntemattomia.
Lukuja $a_{11},\dots,a_{mn}$ nimitetään yhtälöryhmän \emph{kertoimiksi} ja lukuja $b_1,b_2,\dots,b_m$ \emph{vakioiksi}.
Jos tuntemattomia on vähän, niitä merkitään yleensä symboleilla $x,y,z$ ja niin
edelleen.

Esimerkiksi 
\begin{equation*}\label{yhtaloryhmaEsim}
\left\{
\begin{array}{rcrcrcr}
-4x_1&+&\sqrt{3}x_2&+&2x_3&=&4 \\
x_1&&&+&\frac{6}{8}x_3&=&0 \\
5x_1&+&\sqrt{2}x_2&+&11x_3&=&-3 \\
&-&6x_2&-&32x_3&=&4 \\
\end{array}
\right.
\end{equation*}
on lineaarinen yhtälöryhmä.

Lineaarisen yhtälöryhmän ratkaiseminen merkitsee sitä, että löydetään kaikki ne luvut, jotka tuntemattomien $x_1,\dots,x_n$ paikalle
sijoitettuina toteuttavat yhtä aikaa kaikki yhtälöt.

%\subsubsection{Lineaarisen yhtälöryhmän matriisi}

Lineaarisessa yhtälöryhmässä oleellisia ovat vain kertoimet ja vakiot. Kaikki tieto
yhtälöryhmästä voidaankin tiivistää lukutaulukkoon eli \emph{matriisiin}, jossa
luetellaan kaikki kertoimet sekä vakiot. Kun
käsitellään yhtälöryhmien sijasta matriiseja, on kirjoittevaa paljon vähemmän,
sillä tuntemattomia ei tarvitse kirjata ylös.

Esimerkiksi edellä esitellyn yhtälöryhmän matriisi on
\[
\begin{bmatrix}[rrr|r]
-4&\sqrt{3}&2&4 \\
1&0&\frac{6}{8}&0 \\
5&\sqrt{2}&11&-3 \\
0&-6&-32&4
\end{bmatrix}.
\]
Selkeyden vuoksi kertoimet on tapana erottaa vakioista pystyviivalla. Huomaa,
että matriisiin on kirjoitettava nolla niiden termien kohdalle, jotka puuttuvat
yhtälöryhmästä. Kyseisten termien kertoimena on nimittäin nolla.

Kappaleessa 8 tutustutaan matriisien teoriaan yleisemmin. Tässä luvussa käsittelemme vain yhtälöryhmistä saatuja
matriiseja.

\subsection{Gaussin--Jordanin eliminointimenetelmä}

Seuraavaksi käydään läpi menetelmä, jolla voidaan ratkaista mikä tahansa
lineaarinen yhtälöryhmä.
Ideana on muokata yhtälöryhmästä uusia yhtälöryhmiä,
joilla on samat ratkaisut kuin alkuperäisellä yhtälöryhmällä. Viimeisenä saatu
yhtälöryhmä on helppo ratkaista. Koska viimeisen yhtälöryhmän ratkaisut ovat samat kuin alkuperäisen yhtälöryhmän, on alkuperäisen yhtälöryhmän ratkaisut löydetty.

\begin{maar}
Yhtälöryhmiä kutsutaan ekvivalenteiksi, jos niillä on täsmälleen samat
ratkaisut.
\end{maar}

Ryhdymme muokkaamaan yhtälöryhmiä niin kutsutuilla alkeisrivitoimituksilla. Niiden avulla tuotetaan uusia yhtälöryhmiä, jotka ovat ekvivalentteja alkuperäisen yhtälöryhmän kanssa. Koska matriisien käsitteleminen on helpompaa kuin yhtälöryhmien, tehdään alkeisrivitoimitukset matriiseille.
\begin{maar}
Seuraavat kolme operaatiota ovat \emph{alkeisrivitoimituksia}:
\begin{enumerate}
\item Vaihdetaan kahden rivin paikka matriisissa.
\item Kerrotaan jokin rivi nollasta poikkeavalla reaaliluvulla.
\item Lisätään johonkin riviin jokin toinen rivi reaaliluvulla kerrottuna.
\end{enumerate}
\end{maar}
%\begin{maar}
%Seuraavat operaatiot tuottavat uuden yhtälöryhmän, joka on ekvivalentti
%alkuperäisen yhtälöryhmän kanssa:
%\begin{itemize}
%\item[a)] Vaihdetaan kahden rivin paikka.
%\item[b)] Kerrotaan jokin rivi nollasta poikkeavalla reaaliluvulla.
%\item[c)] Lisätään johonkin riviin toinen rivi nollasta
%poikkeavalla reaaliluvulla kerrottuna.
%\end{itemize}
%Näitä operaatioita kutsutaan \emph{alkeisrivitoimituksiksi}.
%\end{maar}

Alkeisrivitoimituksille käytetään tässä materiaalissa seuraavia
lyhennysmerkintöjä
\begin{itemize}
\item
$R_i \leftrightarrow R_j$: vaihdetaan rivien $i$ ja $j$ paikat ($i \neq j$).
\item
$aR_i$: kerrotaan rivi $i$ luvulla $a \neq 0$.
\item
$R_i+bR_j$: lisätään riviin $i$ rivi $j$ luvulla $b$ kerrottuna ($i \neq j$).
\end{itemize}

\begin{esim}
%Tutkitaan
%matriisin
%\[
%\begin{bmatrix}[cc|c]
%-4&3&4 \\
%1&0&0 \\
%5&3&-3 \\
%0&-6&4
%\end{bmatrix}
%\]
%avulla, miltä alkeisrivitoimitukset näyttävät:
Seuraavassa on annettu esimerkit erilaisista alkeisrivitoimituksista:
\[
\begin{split}
\begin{bmatrix}[rr|r]
-4&3&4 \\
1&2&-1 \\
5&3&2 \\
0&6&4
\end{bmatrix}
\overset{R_1 \leftrightarrow R_2}{\longrightarrow}
\begin{bmatrix}[rr|r]
1&2&-1 \\
-4&3&4 \\
5&3&2 \\
0&6&4
\end{bmatrix}
\overset{R_3-5R_1}{\longrightarrow}
\begin{bmatrix}[rr|r]
1&2&-1 \\
-4&3&4 \\
0&-7&7 \\
0&6&4
\end{bmatrix}
\overset{-\frac{1}{7}R_3}{\longrightarrow}
\begin{bmatrix}[rr|r]
1&2&-1 \\
-4&3&4 \\
0&1&-1 \\
0&6&4
\end{bmatrix}\\
\end{split}
\]
\end{esim}

\begin{center}
\begin{figure}[hbt!]
\centering
\includegraphics[scale = 1]{Kuvat/kuva75.eps}
\caption{Gaussin-Jordanin eliminointimenetelmän perusta. \label{k75}}
\end{figure}
\end{center}

\begin{maar}
Matriisi $A$ on \emph{riviekvivalentti} matriisin $B$ kanssa, jos $B$ saadaan
matriisista $A$ alkeisrivitoimituksilla.
\end{maar}

Esimerkiksi edellisen esimerkin matriisit
\[
\begin{bmatrix}[rr|r]
-4&3&4 \\
1&2&-1 \\
5&3&2 \\
0&6&4
\end{bmatrix}
\quad \text{ja} \quad
\begin{bmatrix}[rr|r]
1&2&-1 \\
-4&3&4 \\
0&1&-1 \\
0&6&4
\end{bmatrix}
\]
ovat riviekvivalentit. Alkeisrivitoimituksia voidaan ajatella tehtävän myös nolla kappaletta. Siten jokainen matriisi on itsensä kanssa riviekvivalentti.

\begin{lause} \label{ekvivalenttiLause}
Jos yhtälöryhmiä vastaavat matriisit ovat riviekvivalentit, yhtälöryhmät ovat ekvivalentit.
\end{lause}
Lause voidaan muotoilla myös toisin: jos yhtälöryhmiä vastaavat matriisit ovat riviekvivalenit, yhtälöryhmillä on täsmälleen samat ratkaisut.
Alkeisrivitoimituksen tekeminen ei siis muuta yhtälöryhmän ratkaisuja.
Lauseen todistus on esitetty luvun lopussa.
%Lauseen todistus on hieman raskaslukuinen, ja sen voikin sivuuttaa ensimmäisellä lukukerralla.

Yhtälöryhmää ratkaistaessa on tavoitteena muuttaa yhtälöryhmän
matriisi alkeisrivitoimituksilla niin kutsutuksi redusoiduksi porrasmatriisiksi,
josta ratkaisut on helppo nähdä.
Tutustutaan aluksi porrasmatriiseihin ja siirrytään sitten tutkimaan
redusoituja porrasmatriiseja.
\begin{maar}
Matriisi on \emph{porrasmatriisi}, jos
\begin{itemize}
\item[1.] mahdolliset nollarivit ovat alimpina.
\item[2.] kullakin rivillä ensimmäinen nollasta poikkeava alkio (eli \emph{johtava alkio}) on ylemmän rivin johtavan alkion
oikealla puolella.
\end{itemize}
\end{maar}

Esimerkiksi seuraavat matriisit ovat porrasmatriiseja. Niiden johtavat alkiot on lihavoitu.
\[
\begin{bmatrix}[rrrr]
\textbf{14}&3&2&4 \\
0&0&\textbf{8}&0 \\
0&0&0&\textbf{-3} \\
0&0&0&0
\end{bmatrix} \quad
\begin{bmatrix}[rrrrrr]
0&0&\textbf{4}&0&0&-3 \\
0&0&0&\textbf{-1}&7&-11 \\
0&0&0&0&1&\textbf{-3} \\
\end{bmatrix} \quad
\begin{bmatrix}[rrrrrr]
\textbf{-3}&-41&1&0&-3&6 \\
0&0&0&0&\textbf{5}&-11 \\
0&0&0&0&0&0 \\
\end{bmatrix}
\]

\begin{maar}
Matriisi on \emph{redusoitu porrasmatriisi}, jos
\begin{itemize}
\item[1.] se on porrasmatriisi.
\item[2.] jokaisen rivin johtava alkio on 1.
\item[3.] jokainen johtava alkio on sarakkeensa ainoa nollasta poikkeava alkio.
\end{itemize}
\end{maar}

Esimerkiksi seuraavat matriisit ovat redusoituja porrasmatriiseja:
\[
\begin{bmatrix}[rrrr]
1&0&0&4 \\
0&1&0&0 \\
0&0&1&-3 \\
0&0&0&0
\end{bmatrix} \quad
\begin{bmatrix}[rrrrrrr]
0&0&1&-53&0&0&-3 \\
0&0&0&0&1&0&-11 \\
0&0&0&0&0&1&-3 \\
\end{bmatrix} \quad
\begin{bmatrix}[rrrrrr]
1&3&0&0&-3&8 \\
0&0&1&-3&5&-11 \\
0&0&0&0&0&0 \\
\end{bmatrix}
\]

\begin{esim}
Matriisi
\[
\begin{bmatrix}[rrr|r]
1 & 0 & 0 & 4 \\
0 & 1 & 0 & -2 \\
0 & 0 & 1 & 3 \\
\end{bmatrix}
\]
on redusoitu porrasmatriisi. Sitä vastaava yhtälöryhmä on
\begin{equation*}
%\left\{
%\begin{array}{rrrcr}
%x_1&&&=&4 \\
%&x_2&&=&-2 \\
%&&x_3&=&3.
%\end{array}
%\right.
\left\{
\begin{aligned}
x_1\phantom{{}+x_2+x_3}&=4 \\
x_2 \phantom{{}+x_3}&=-2 \\
x_3&=3.
\end{aligned}
\right.
\end{equation*}
Huomataan, että yhtälöryhmästä näkyy suoraan sen ratkaisu, joka on
\begin{equation*}
\left\{
%\begin{array}{rcr}
%x_1&=&4 \\
%x_2&=&-2 \\
%x_3&=&3. \\
%\end{array}
\begin{aligned}
x_1&=4 \\
x_2&=-2 \\
x_3&=3.
\end{aligned}
\right.
\end{equation*}
Ratkaisut on helppo nähdä juuri sen vuoksi, että yhtälöryhmän matriisi on
redusoitu porrasmatriisi.
\end{esim}

Tavoitteena on siis muuttaa yhtälöryhmän matriisi redusoiduksi porrasmatriisiksi, josta ratkaisut näkyvät suoraan. Voidaan osoittaa, että mikä tahansa matriisi voidaan muuttaa alkeisrivitoimituksilla redusoiduksi
porrasmatriisiksi. Seuraava esimerkki näyttää, kuinka tämä tehdään.

\begin{esim}\label{redusoituPorrasEsim}
%\[
%\begin{bmatrix}
%1&0&2&1\\
%2&-1&3&2\\
%-1&-2&0&3
%\end{bmatrix}\]
%ja muutetaan se redusoiduksi porrasmatriisiksi.
%Aloitetaan ensimmäisestä sarakkeesta. Ensimmäisen rivin johtavan alkion alla
%pitäisi olla pelkkiä nollia. Nollat saadaan aikaan ensimmäisen rivin johtavan
%alkion avulla. Lisätään toiseen riviin ensimmäinen rivi luvulla $-2$ kerrottuna:
Tutkitaan matriisia
\[
\begin{bmatrix}[rrrr]
2&-1&3&2\\
1&0&2&1\\
-1&-2&0&3
\end{bmatrix}\]
ja muutetaan se redusoiduksi porrasmatriisiksi.
Aloitetaan ensimmäisestä sarakkeesta. Vaihtamalla ensimmäisen ja toisen rivin paikat, saadaan ensimmäisen rivin johtavaksi alkioksi 1:
\[
\overset{R_1 \leftrightarrow R_2}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
2&-1&3&2\\
-1&-2&0&3
\end{bmatrix}.\]
Tämän jälkeen johtavan alkion alla olevat alkiot on helppo muuttaa nolliksi. Vähennetään ensin toisesta rivistä ensimmäinen rivi luvulla $2$ kerrottuna:
\[
\overset{R_2-2R_1}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&-1&-1&0\\
-1&-2&0&3
\end{bmatrix} .\]
Lisätään sitten kolmanteen riviin ensimmäinen rivi luvulla 1 kerrottuna:
\[
\overset{R_3+R_1}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&-1&-1&0\\
0&-2&2&4
\end{bmatrix}.
\]
Nyt ensimmäinen sarake on halutussa muodossa. Siirrytään muokkaaman toista
saraketta. Muutetaan ensin sen johtava alkio ykköseksi, jotta voidaan toimia
samoin kuin edellä. Kerrotaan siis toinen rivi luvulla $-1$.
%Tätä operaatiota voidaan merkitä $-1 \cdot R_2$.
Saadaan matriisi
\[
\overset{-1 \cdot R_2}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&1&1&0\\
0&-2&2&4
\end{bmatrix}.
\]
Toisen rivin johtavan alkion avulla voidaan muuttaa sen alla oleva alkio nollaksi. Lisätään
kolmanteen riviin toinen rivi luvulla 2 kerrottuna. Saadaan matriisi
\[
\overset{R_3+2R_2}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&1&1&0\\
0&0&4&4
\end{bmatrix},
\]
joka on porrasmatriisi.

Jatketaan muokkaamista niin, että saadaan aikaan redusoitu porrasmatriisi.
Muutetaan ensin kaikki johtavat alkiot ykkösiksi:
\[
\overset{\frac{1}{4}R_3}{\longrightarrow}
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&1&1&0\\
0&0&1&1
\end{bmatrix}.
\]
Muutetaan alimman rivin johtavan alkion avulla kaikki kolmannen sarakkeen
muut alkiot nolliksi:
\[\begin{split}
\overset{R_2-R_3}{\longrightarrow} &
\begin{bmatrix}[rrrr]
1&0&2&1\\
0&1&0&-1\\
0&0&1&1
\end{bmatrix} 
\overset{R_1-2R_3}{\longrightarrow} 
\begin{bmatrix}[rrrr]
1&0&0&-1\\
0&1&0&-1\\
0&0&1&1
\end{bmatrix}.
\end{split}
\]
Näin saatu matriisi on redusoitu porrasmatriisi.

Saatu redusoitu porrasmatriisi on eri matriisi kuin se, josta lähdettiin
liikkeelle. Matriisit myös vastaavat erilaisia yhtälöryhmiä. Näillä
yhtälöryhmillä on kuitenkin samat ratkaisut.
\end{esim}

%Ei ole selvää, että jokainen matriisi voidaan muuttaa alkeisrivitoimituksilla
%redusoiduksi porrasmatriisiksi. Niin voidaan kuitenkin tehdä, vaikka asiaa ei
%tässä todistetakaan. Ei ole kuitenkaan vaikea vakuuttua siitä, että %esimerkissä \ref{redusoituPorrasmuotoEsim} käytetty menetelmä toimii millä %tahansa matriisilla.


Ohjeita redusoidun porrasmatriisin aikaansaamiseksi:
\begin{itemize}
\item Porrasmatriisia muodostetaan vasemmalta oikealle ja ylhäältä alaspäin.
\item Johtavat alkiot kannattaa useimmiten muuttaa ykkösiksi.
\item Johtavien alkioiden avulla muutetaan niiden alapuolella olevat alkiot
nolliksi. Näin saadaan aikaan porrasmatriisi.
\item Redusoitua porrasmatriisia muodostetaan oikealta vasemmalle ja alhaalta
ylöspäin.
\item Johtavien alkioiden avulla muutetaan niiden yläpuolella olevat alkiot nolliksi.
\item Tee vain yksi alkeisrivitoimitus kerrallaan!
\end{itemize}

\subsubsection*{Gaussin-Jordanin menetelmä}

Nyt olemme valmiita ottamaan käyttöön niin kutsutun Gaussin-Jordanin menetelmän, jonka avulla lineaariset yhtälöryhmät voidaan aina ratkaista.
\begin{enumerate}
\item Kirjoita yhtälöryhmän matriisi.
\item Muuta matriisi alkeisrivitoimituksilla porrasmatriisiksi.
\item Muuta porrasmatriisi redusoiduksi porrasmatriisiksi.
\item Lue ratkaisut redusoidusta porrasmatriisista.
\end{enumerate}

\begin{esim}
Ratkaistaan yhtälöryhmä
\begin{equation*}
\left\{
\begin{array}{rcrcrcl}
2x_1&-&x_2&+&3x_3&=&2 \\
x_1&&&+&2x_3&=&1 \\
-x_1&-&2x_2&&&=&3. \\
\end{array}
\right.
\end{equation*}
Sen matriisi on
\[
\begin{bmatrix}[rrr|r]
2&-1&3&2\\
1&0&2&1\\
-1&-2&0&3
\end{bmatrix}\]
Tämä matriisi muutettiin redusoituksi porrasmatriisiksi esimerkissä \ref{redusoituPorrasmuotoEsim}:
\[
\begin{bmatrix}[rrr|r]
1&0&0&-1\\
0&1&0&-1\\
0&0&1&1
\end{bmatrix}.
\]
Redusoitua porrasmatriisia vastaava yhtälöryhmä on
\begin{equation*}
\left\{
\begin{array}{rrrcl}
x_1&&&=&-1 \\
&x_2&&=&-1 \\
&&x_3&=&1. \\
\end{array}
\right.
\end{equation*}
Koska alkuperäisen yhtälöryhmän ratkasut ovat lauseen \ref{ekvivalenttiLause} nojalla samat kuin lopuksi saadun yhtälöryhmän, on yhtälöryhmä ratkaistu. Sen ratkaisu on
\begin{equation*}
\left\{
\begin{array}{rcl}
x_1&=&-1 \\
x_2&=&-1 \\
x_3&=&1. \\
\end{array}
\right.
\end{equation*}
\end{esim}

%\begin{esim}
%Ratkaistaan lineaarinen yhtälöryhmä
%\[
%\left\{
%\begin{aligned}
%-3x+5y&=-22 \\
%3x+4y&=4 \\
%4x-8y&=32.
%\end{aligned}
%\right.
%\]
%\end{esim}

\begin{esim}
Ratkaistaan lineaarinen yhtälöryhmä
\[
\left\{
\begin{aligned}
x+2y+z&=8 \\
-3x-6y -3z&=-21.
\end{aligned}
\right.
\]
Muutetaan sen matriisi redusoiduksi porrasmatriisiksi:
\[
\begin{bmatrix}[rrr|r]
1 & 2 & 1 & 8 \\
-3 & -6 & -3 & -21
\end{bmatrix}
\overset{R_2+3R_1}{\longrightarrow}
\begin{bmatrix}[rrr|r]
1 & 2 & 1 & 8 \\
0 & 0 & 0 & 3
\end{bmatrix}
\]
Vastaava yhtälöryhmä on
\[
\left\{
\begin{aligned}
x+2y+z&=8 \\
0&=3.
\end{aligned}
\right.
\]
Alin yhtälö on aina epätosi, joten yhtälöryhmällä ei ole ratkaisua.
\end{esim}

\begin{esim}
Ratkaistaan lineaarinen yhtälöryhmä
\[
\left\{
\begin{aligned}
3x_1+3x_2-15x_3&=9 \\
x_1\phantom{{}+3x_2}-\phantom{1}2x_3&=1 \\
2x_1-\phantom{3}x_2-\phantom{15}x_3&=0\,.
\end{aligned}
\right.
\]
Muutetaan sen matriisi redusoiduksi porrasmatriisiksi:
\begin{alignat*}{4}
& & &\begin{bmatrix}[rrr|r]
3 & 3 & -15 & 9 \\
1 & 0 & -2 & 1 \\
2 & -1 & -1 & 0
\end{bmatrix}
&\  &\overset{\frac{1}{3}R_1}{\longrightarrow} &\ 
&\begin{bmatrix}[rrr|r]
1 & 1 & -5 & 3 \\
1 & 0 & -2 & 1 \\
2 & -1 & -1 & 0
\end{bmatrix} \\[1mm]
&\overset{R_2-R_1}{\longrightarrow} &\ 
&\begin{bmatrix}[rrr|r]
1 & 1 & -5 & 3 \\
0 & -1 & 3 & -2 \\
2 & -1 & -1 & 0
\end{bmatrix}
& &\overset{R_3 - 2R_1}{\longrightarrow}
& &\begin{bmatrix}[rrr|r]
1 & 1 & -5 & 3 \\
0 & -1 & 3 & -2 \\
0 & -3 & 9 & -6
\end{bmatrix} \\[1mm]
&\overset{-1 \cdot R_2}{\longrightarrow}
& &\begin{bmatrix}[rrr|r]
1 & 1 & -5 & 3 \\
0 & 1 & -3 & 2 \\
0 & -3 & 9 & -6
\end{bmatrix}
& &\overset{R_3+3R_2}{\longrightarrow}
& &\begin{bmatrix}[rrr|r]
1 & 1 & -5 & 3 \\
0 & 1 & -3 & 2 \\
0 & 0 & 0 & 0
\end{bmatrix} \\[1mm]
&\overset{R_1-R_2}{\longrightarrow}
& &\begin{bmatrix}[rrr|r]
1 & 0 & -2 & 1 \\
0 & 1 & -3 & 2 \\
0 & 0 & 0 & 0
\end{bmatrix}
\end{alignat*}

Saatua matriisia vastaa yhtälöryhmä
\[
\left\{
\begin{aligned}
x_1-2x_3&=1 \\
x_2-x_3&=2\\
0&=0
\end{aligned}
\right.
\]
Alin yhtälö $0 = 0$ on aina tosi. Tuntemattomalle $x_3$ ei puolestaan aseteta mitään rajoitteita, joten se voi olla mikä tahansa reaaliluku. Sanotaan, että $x_3$ on \emph{vapaa muuttuja}. Merkitään $x_3 = t$, missä $t \in \R$.  Ratkaistaan vielä muut tuntemattomat. Ylin yhtälö saadaan muotoon $x_1- 2t=1$, joten $x_1=1+2t$. Toinen yhtälö puolestaan on $x_2-t=2$ eli $x_2=2+t$. Siten yhtälön ratkaisu on
\[
\left\{
\begin{aligned}
x_1 &=1 + 2t \\
x_2&=2 + t \\
x_3 &= t,
\end{aligned}
\right.
\]
missä $t \in \R$.
Ratkaisuja on siis äärettömän monta. Esimerkiksi $x_1 = 3$, $x_2 = 3$ ja $x_3 = 1$ sekä $x_1 = -1$, $x_2 = 1$ ja $x_3 = -1$ ovat yhtälöryhmän ratkaisuja. Jokaisella reaaliluvulla $t$ yhtälöryhmälle saadaan eri ratkaisu.

Huomaa, että vapaat muuttujat näkyvät redusoidussa porrasmatriisissa sarakkeina, joissa ei ole lainkaan johtavaa alkiota.

\end{esim}

\begin{esim}
Lineaarisen yhtälöryhmän matriisi muutettiin alkeisrivitoimituksilla redusoiduksi porrasmatriisiksi
\[\begin{bmatrix}[cccccc|c]
1&3&0&4&0&0&7\\
0&0&1&2&0&0&0\\
0&0&0&0&0&1&3\\
\end{bmatrix}.\]
Mikä on yhtälöryhmän ratkaisu?

Havaitaan, että johtavat alkiot ovat sarakkeissa 1, 3 ja 6. Muita sarakkeita vastaavat tuntemattomat $x_2$, $x_4$ ja $x_5$ ovat vapaita muuttujia. Merkitään $x_2=r$, $x_4 = s$ ja $x_5 = t$, missä $r$, $s$, $t \in \R$. 

Nyt voidaan kirjoittaa
\[
\left\{
\begin{aligned}
x_1+3r+4s&=7 \\
x_3+2s&=0 \\
x_6&=3
\end{aligned}
\right.
\]
ja edelleen
\[
\left\{
\begin{aligned}
x_1 &=7-3r-4s \\
x_3&=-2s \\
x_6 &= 3. 
\end{aligned}
\right.
\]
Yhtälöryhmän ratkaisu on siis
\[
\left\{
\begin{aligned}
x_1 &=7-3r-4s \\
x_2 &= r \\
x_3&=-2s \\
x_4 &= s \\
x_5 &= t \\
x_6 &= 3, 
\end{aligned}
\right.
\]
missä $r, s, t \in \R$.
\end{esim}

Esimerkeistä huomataan, että yhtälöryhmällä voi olla täsmälleen yksi ratkaisu, äärettömän monta ratkaisua tai 
ei yhtään ratkaisua. Kun muuttujia on kaksi, tilannetta voi havainnollistaa kuvan avulla.
Tutkitaan yhtälöparia
\begin{equation*}
\left\{
\begin{aligned}
ax+by&=c \\
dx+ey&=f.
\end{aligned}
\right.
\end{equation*}
Oletetaan, että yhtälöllä on ratkaisu $x=r$, $y=s$. Sitä voidaan ajatella tason pisteenä $(r,s)$. Koska ratkaisu toteuttaa ensimmäisen yhtälön, piste $(r,s)$ on suoralla, jonka yhtälö on $ax+by=c$. Samoin piste $(r,s)$ on suoralla, jonka yhtälö on $dx+ey=f$. Piste $(r,s)$ on siis molemmilla suorilla, eli se on suorien leikkauspiste.

Jos yhtälöt määrittävät kaksi erisuuntaista suoraa, on niillä on täsmälleen yksi leikkauspiste. Tällöin yhtälöparilla on täsmälleen yksi ratkaisu. Jos yhtälöt määrittävät saman suoran, on leikkauspisteitä äärettömän monta. Silloin ratkaisujakin on äärettömän monta. Jos yhtälöiden määrittämät suorat eivät ole samat mutta ovat kuitenkin yhdensuuntaiset, ei leikkauspisteitä ole. Silloin ei myöskään yhtälöparilla ole ratkaisuja.
\begin{center}
\begin{figure}[hbt!]
\centering
\includegraphics[scale = 1]{Kuvat/kuva76.eps}
\caption{Yhtälöryhmällä on tasan yksi ratkaisu, äärettömän monta ratkaisua tai ei yhtään ratkaisua. \label{k76}}
\end{figure}
\end{center}

\begin{esim}
Tarkastellaan yhtälöryhmää
\[
\left\{
\begin{aligned}
x+\phantom{k}y+kz&=1 \\
x+ky+\phantom{k}z&=1 \\
kx+\phantom{k}y+\phantom{k}z&=-2\,.
\end{aligned}
\right.
\]

Tutkitaan, miten luvun $k$ arvot vaikuttavat ratkaisujen lukumäärään. Ryhdytään muuttamaan yhtälöryhmän matriisia redusoiduksi porrasmatriisiksi:

\begin{align*}
& \begin{bmatrix}[rrr|r]
1&1&k&1\\ 
1&k&1&1\\
k&1&1&-2\\
\end{bmatrix} \overset{R_2-R_1}{\longrightarrow} 
\begin{bmatrix}[rrr|r]
1&1&k&1\\ 
0&k-1&1-k&0\\
k&1&1&-2\\
\end{bmatrix} \\
\overset{R_3-kR_1}{\longrightarrow}
&\begin{bmatrix}[rrr|r]
1&1&k&1\\ 
0&k-1&1-k&0\\
0&1-k&1-k^2&-2-k\\
\end{bmatrix}
\overset{R_3+R_2}{\longrightarrow}
\begin{bmatrix}[rrr|r]
1&1&k&1\\ 
0&k-1&1-k&0\\
0&0&2-k-k^2&-2-k\\
\end{bmatrix}
\end{align*}

%Nyt joudutaan tarkastelemaan erilaisia vaihtoehtoja sen mukaan, onko $k-1$ nolla vai ei.
Kaikki alkeisrivitoimitukset voidaan tähän asti tehdä riippumatta siitä, mikä luku $k$ on. Jatkaminen ei kuitenkaan onnistu, sillä toisen rivin alkio $k - 1$ saattaa olla nolla, samoin kolmannen rivin alkio $2 - k - k^2$. Tarkastellaan näitä tapauksia erikseen.

Oletetaan ensin, että kolmannen rivin alkio $2 - k - k^2 = 0$ eli $k = -2$ tai $k = 1$. 
\begin{itemize}
\item Jos $k = -2$, viimeinen matriisi on 
\[\begin{bmatrix}[rrr|r]
1&1&-2&1\\ 
0&-3&3&0\\
0&0&0&0\\
\end{bmatrix}.\]
Havaitaan, että alinta riviä vastaava yhtälö $0 = 0$ on aina tosi. Lisäksi tuntematonta $x_3$ vastaavassa sarakkeessa ei ole johtavaa alkiota, joten $x_3$ on vapaa muuttuja. Ratkaisuja on siten äärettömän monta.
\item Jos $k = 1$, viimeinen matriisi on 
\[\begin{bmatrix}[rrr|r]
1&1&1&1\\ 
0&0&0&0\\
0&0&0&-3\\
\end{bmatrix}.\]
Havaitaan, että alinta riviä vastaava yhtälö $0 = -3$ on aina epätosi. Siten yhtälöryhmällä ei ole ratkaisuja.
\end{itemize}

Oletetaan sitten, että toisen rivin alkio $k-1 = 0$ eli $k = 1$. Tämä tapaus käsiteltiin sattumalta jo edellä. 

Tarkastellaan vielä lopuksi tilannetta, jossa sekä toisen rivin alkio $k-1$ että kolmannen rivin alkio $2 - k - k^2$ ovat nollasta poikkeavia. Tällöin voidaan jatkaa alkeisrivitoimitusten tekemistä.
Koska $k-1 \neq 0$ ja $2 - k - k^2 \neq 0$ saadaan
\[
\overset{\frac{1}{k-1}R_2}{\longrightarrow}
\begin{bmatrix}[rrr|r]
1&1&k&1\\ 
0&1&-1&0\\
0&0&2-k-k^2&-2-k\\
\end{bmatrix} \overset{\frac{1}{2 - k - k^2}R_3}{\longrightarrow}
\begin{bmatrix}[rrr|r]
1&1&k&1\\ 
0&1&-1&0\\
0&0&1&(-2-k)/(2 - k - k^2)\\
\end{bmatrix}.
\]
Tällöin yhtälöryhmällä on täsmälleen yksi ratkaisu. %Nähdään nimittäin, että $x_3 = (-2-k)/(2-k-k^2)$ ja ylemmistä yhtälöistä saadaan muut tuntemattomat.

%Jos kerroin $2-k-k^2$ on nolla eli $k = -2$, on periaatteessa kaksi mahdollisuutta:
%\begin{enumerate*}
%\item Pätee $-2-k = 0$ eli $k = -2$. Tällöin yhtälöllä on äärettömän monta ratkaisua. Alinta riviä nimittäin vastaa yhtälö $0 = 0$ ja $x_3$ %on vapaa muuttuja.
%\item Pätee $-2-k \neq 0$ eli $k \neq -2$. Tämä on kuitenkin mahdotonta, sillä oletimme, että $k = -2$.
%\end{enumerate*}

%Oletetaan sitten, että $k-1 = 0$ eli $k = 1$. Alkuperäinen
%yhtälöryhmä on tällöin
%\[
%\left\{
%\begin{aligned}
%x+y+z&=1 \\
%x+y+z&=1 \\
%x+y+z&=-2\,.
%\end{aligned}
%\right.
%\]
%Ylin ja alin yhtälö ovat keskenään ristiriitaiset, joten yhtälöryhmällä ei ole ratkaisua.

Päädyttiin siis seuraavaan tulokseen: Yhtälöryhmällä on äärettömän monta ratkaisua, jos ja vain jos $k = -2$. Yhtälöryhmällä ei ole ratkaisua, jos ja vain jos $k = 1$. Yhtälöryhmällä on tasan yksi ratkaisu, jos ja vain jos $k \neq 1$ ja $k \neq -2$. 
\end{esim}

Käydään vielä lopuksi läpi lauseen 5.5 todistus, joka sivuutettiin luvun alussa.

\begin{proof}
Osoitetaan, että jos yhtälöryhmiä vastaavat matriisit ovat riviekvivalentit, yhtälöryhmät ovat ekvivalentit. Tätä varten riittää näyttää, että alkeisrivitoimituksen tekeminen ei vaikuta yhtälöryhmän ratkaisuihin. Tutkitaan yhtälöryhmää

\begin{equation}\label{eiKerrottu}
\left\{
\begin{array}{rcrcccrcr}
a_{11}x_1&+&a_{12}x_2&+&\dots&+&a_{1n}x_n&=&b_1 \\
&&&&&&&\vdots & \\
a_{i1}x_1&+&a_{i2}x_2&+&\dots&+&a_{in}x_n&=&b_i \\
&&&&&&&\vdots & \\
a_{m1}x_1&+&a_{m2}x_2&+&\dots&+&a_{mn}x_n&=&b_m, \\
\end{array}
\right.
\end{equation}
missä $a_{11},\dots,a_{mn},b_1,\dots,b_m \in \R$.

1. Ensinnäkin huomataan, että yhtälöryhmän rivien järjestyksellä ei ole väliä. Siten kahden rivin paikkojen vaihtaminen ei muuta yhtälöryhmän ratkaisuja.

2. Tutkitaan sitten alkeisrivitoimitusta, joka kertoo rivin $i$ luvulla $c \in \R \setminus\{0\}$. Tuloksena on yhtälöryhmä

\begin{equation}\label{kerrottu}
\left\{
\begin{array}{rcrcccrcr}
a_{11}x_1&+&a_{12}x_2&+&\cdots&+&a_{1n}x_n&=&b_1 \\
&&&&&&&\vdots & \\
ca_{i1}x_1&+&ca_{i2}x_2&+&\cdots&+&ca_{in}x_n&=&cb_i \\
&&&&&&&\vdots & \\
a_{m1}x_1&+&a_{m2}x_2&+&\cdots&+&a_{mn}x_n&=&b_m. \\
\end{array}
\right.
\end{equation}

On osoitettava, yhtälöryhmillä (\ref{eiKerrottu}) ja (\ref{kerrottu}) on samat ratkaisut. Tämä tehdään kahdessa osassa. Ensin näytetään, että jokainen yhtälöryhmän (\ref{eiKerrottu}) ratkaisu on myös yhtälöryhmän (\ref{kerrottu}) ratkaisu. Sitten näytetään, että jokainen yhtälöryhmän (\ref{kerrottu}) ratkaisu on myös yhtälöryhmän (\ref{eiKerrottu}) ratkaisu.

Oletetaan ensin, että $x_1=r_1, \dots, x_n=r_n$ on yhtälöryhmän (\ref{eiKerrottu})
ratkaisu ja osoitetaan, että se on myös ryhmän (\ref{kerrottu}) ratkaisu. Oletuksen perusteella pätee
\begin{equation*}
\left\{
\begin{array}{rcrcccrcl}
a_{11}r_1&+&a_{12}r_2&+&\cdots&+&a_{1n}r_n&=&b_1 \\
&&&&&&&\vdots & \\
a_{i1}r_1&+&a_{i2}r_2&+&\cdots&+&a_{in}r_n&=&b_i \\
&&&&&&&\vdots & \\
a_{m1}r_1&+&a_{m2}r_2&+&\cdots&+&a_{mn}r_n&=&b_m. \\
\end{array}
\right.
\end{equation*}
Kun $i$:nnen yhtälön molemmat puolet kerrotaan luvulla $c$, saadaan yhtälö \[ca_{i1}r_1+\cdots +ca_{in}r_n=cb_i.\]
Nyt siis $x_1=r_1, \dots x_n=r_n$ toteuttaa yhtälöryhmän (\ref{kerrottu}), ja siten se on myös yhtälöryhmän (\ref{kerrottu})
ratkaisu.

Oletetaan sitten, että $x_1=s_1, \dots, x_n=s_n$ on yhtälöryhmän (\ref{kerrottu})
ratkaisu ja osoitetaan, että se on myös ryhmän (\ref{eiKerrottu}) ratkaisu. Nyt siis
\begin{equation*}
\left\{
\begin{array}{rcrcccrcl}
a_{11}s_1&+&a_{12}s_2&+&\cdots&+&a_{1n}s_n&=&b_1 \\
&&&&&&&\vdots & \\
ca_{i1}s_1&+&ca_{i2}s_2&+&\cdots&+&ca_{in}s_n&=&cb_i \\
&&&&&&&\vdots & \\
a_{m1}s_1&+&a_{m2}s_2&+&\cdots&+&a_{mn}s_n&=&b_m. \\
\end{array}
\right.
\end{equation*}
Koska $c \neq 0$, voidaan $i$:nnen yhtälön molemmat puolet jakaa luvulla $c$. Tällöin saadaan yhtälö $a_{i1}s_1+\cdots +a_{in}s_n=b_i$. Nyt nähdään, että $x_1=s_1, \dots, x_n=s_n$ toteuttaa myös yhtälöryhmän (\ref{eiKerrottu}), joten se on myös yhtälöryhmän (\ref{eiKerrottu})
ratkaisu. Siten yhtälöryhmillä on samat ratkaisut.

3. Kolmannen alkeisrivitoimituksen tarkastelu jätetään lukijalle.

\begin{comment}
Väitettä ei todisteta tässä tarkasti. Käydään kuitenkin todistus läpi yhdelle
alkeisrivitoimituksista siinä tapauksessa, että yhtälöryhmässä on kaksi yhtälöä
ja kaksi tuntematonta. Yleinen tapaus todistetaan samaan tapaan.
%Tämän erikoistapauksen todistuksesta näkyy, millä tavoin väite osoitetaan.

Tarkastellaan yhtälöryhmää
\begin{equation} \label{ryhma1}
\left\{
\begin{array}{rcrcl}
a_{11}x_1&+&a_{12}x_2&=&b_1 \\
a_{21}x_1&+&a_{22}x_2&=&b_2.
\end{array}
\right.
\end{equation}
Olkoon $c \in \R$. Kun yhtälöryhmälle tehdään alkeisrivitoimitus $R_2+cR_1$
saadaan yhtälöryhmä
\begin{equation} \label{ryhma2}
\left\{
\begin{array}{rcrcl}
a_{11}x_1&+&b_{12}x_2&=&b_1 \\
(ca_{11}+a_{21})x_1&+&(ca_{12}+a_{22})x_2&=&b_2+cb_1.
\end{array}
\right.
\end{equation}
Nyt on osoitettava, että näillä kahdella yhtälöryhmällä on samat ratkaisut. Tämä tehdään kahdessa osassa. Ensin näytetään, että jokainen yhtälöryhmän (\ref{ryhma1}) ratkaisu on myös yhtälöryhmän (\ref{ryhma2}) ratkaisu. Sitten näytetään, että jokainen yhtälöryhmän (\ref{ryhma2}) ratkaisu on myös yhtälöryhmän (\ref{ryhma1}) ratkaisu.

Oletetaan ensin, että $x_1=r_1$, $x_2=r_2$ on yhtälöryhmän (\ref{ryhma1})
ratkaisu ja osoitetaan, että se on myös ryhmän (\ref{ryhma2}) ratkaisu. Oletuksen perusteella pätee
\begin{equation*}
\left\{
\begin{array}{rcrcl}
a_{11}r_1&+&a_{12}r_2&=&b_1 \\
a_{21}r_1&+&a_{22}r_2&=&b_2.
\end{array}
\right.
\end{equation*}
Kun toisen ensimmäisen molemmat puolet kerrotaan luvulla $c$, saadaan $ca_{11}r_1+ca_{12}r_2=cb_1$. Lasketaan tämä puolittain yhteen ensimmäisen yhtälön kanssa. Tuloksena on
\[(ca_{11}c+a_{21})x_1+(a_{12}+ca_{22})x_2=b_2+cb_1.\]
Siis pätee
\begin{equation*}
\left\{
\begin{array}{rcrcl}
a_{11}r_1&+&b_{12}r_2&=&b_1 \\
(ca_{11}+a_{21})r_1&+&(ca_{12}+a_{22})r_2&=&b_2+cb_1.
\end{array}
\right.
\end{equation*}
ja näin ollen $x_1=r_1$, $x_2=r_2$ on yhtälöryhmän (\ref{ryhma2}) ratkaisu.

Oletetaan sitten, että $x_1=r_1$, $x_2=r_2$ on yhtälöryhmän (\ref{ryhma2})
ratkaisu. Samalla tavalla kuin edellä voidaan osoittaa, että  $x_1=r_1$, $x_2=r_2$ on myös yhtälöryhmän (\ref{ryhma2}) ratkaisu. Tämä jätetään lukijalle. 
\end{comment}

\begin{comment}
ja osoitetaan, että se on myös ryhmän \ref{ryhma1} ratkaisu. Nyt
\begin{equation*}
\left\{
\begin{array}{rcrcr}
a_{11}r_1&+&b_{12}r_2&=&b_1.
(ca_{11}+a_{21})r_1&+&(ca_{12}+a_{22})r_2&=&b_2+cb_1 \\
\end{array}
\right.
\end{equation*}
Kerrotaan ylempi yhtälö luvulla $-1$ ja lisätään se alempaan yhtälöön.
Näin saadaan $ca_{11}r_1+ca_{22}r_2=cb_2$. Jaetaan tämä luvulla $c$. Nyt tiedetään, että $a_{21}r_1+a_{22}r_2=b_2$. Siis
\begin{equation*}
\left\{
\begin{array}{rcrcr}
a_{11}r_1&+&a_{12}r_2&=&b_1 \\
a_{21}r_1&+&a_{22}r_2&=&b_2.
\end{array}
\right.
\end{equation*}
ja siksi $x_1=r_1$, $x_2=r_2$ on yhtälöryhmän \ref{ryhma1} ratkaisu.
\end{comment}
\end{proof}

\begin{comment}

Seuraavaa riviekvivalentteihin matriiseihin liittyvää lausetta tullaan tarvitsemaan jatkossa.

\begin{lause} \label{riviekvLause}
\begin{aakkosta*}
\item
Jos matriisi $A$ on riviekvivalentti matriisin $B$ kanssa, niin matriisi $B$ on riviekvivalentti matriisin $A$ kanssa.
\item
Jos matriisi $A$ on riviekvivalentti matriisin $B$ kanssa ja matriisi $B$ on riviekvivalentti matriisin $C$ kanssa, niin $A$ on riviekvivalentti matriisin $C$ kanssa.
\end{aakkosta*}
\end{lause}

\begin{proof}
a) Käydään läpi todistuksen idea. Oletetaan, että matriisi $A$ on riviekvivalentti matriisin $B$ kanssa. Nyt on olemassa alkeisrivitoimitukset, joiden avulla matriisi $A$ voidaan muuttaa matriisiksi $B$. Jokainen alkeisrivitoimitus voidaan kuitenkin peruuttaa toisella alkeisrivitoimituksella kuten kohta nähdään. Kutsutaan tätä alkeisrivitoimitusta alkuperäisen alkeisrivitoimituksen \emph{käänteistoimitukseksi}.

Oletetaan, että $a,b \in \R$ ja $a \neq 0$. Jos matriisille tehdään alkeisrivitoimitus $R_i \leftrightarrow R_j$, päästään takaisin alkutilanteeseen tekemällä sama alkeisrivitoimitus uudelleen. Alkeisrivitoimitus $R_i \leftrightarrow R_j$ on siis itsensä käänteistoimitus. Alkeisrivitoimituksen $aR_i$ käänteistoimitus on puolestaan $\frac{1}{a}R_i$, ja alkeisrivitoimituksen $R_i+bR_j$ käänteistoimitus on $R_i-bR_j$. 

Matriisille $A$ on siis tehty alkeisrivitoimituksia ja niiden avulla on päädytty matriiisin $B$. Jos matriisille $B$ tehdään samojen alkeisrivitoimitusten käänteistoimitukset päinvastaisessa järjestyksessä, saadaan matriisi $A$. Siten matriisi $B$ on riviekvivalentti matriisin $A$ kanssa.

b) Todistus jätetään harjoitustehtäväksi.
\end{proof}

\end{comment}








Ohjelmoinnin MOOC on verkkokurssi, jossa perehdytään algoritmien laatimiseen ja nykyaikaisen ohjelmoinnin perusideoihin. Opiskelijalta ei edellytetä ennakkotietoja ohjelmoinnista.

- Kurssi vastaa sisällöltään Helsingin yliopiston tietojenkäsittelytieteen laitoksen kursseja [Ohjelmoinnin perusteet](http://www.cs.helsinki.fi/courses/581325/) ja [Ohjelmoinnin jatkokurssi](http://www.cs.helsinki.fi/courses/582103/), jotka ovat 5 opintopisteen laajuisia perusopintotason kursseja.

# Tervetuloa ohjelmoimaan!

Ennen kuin voit aloittaa tehtävien tekemisen, tulee sinun suorittaa muutamia aloitustoimenpiteitä.

<div class="actions">
    <a class="action primary" href="/courses/general/ohjelmointi/asentaminen/" target="_blank">Asennusohjeisiin</a>
</div>

# Valitse oikea kurssi

Suoritettuasi asennutoimenpiteet valitse TMC:n asetuksista kurssi **<em>2015-nodl-ohjelmointi</em>**. 

Kurssilla ei ole viikoittaisia deadlineja, vaan seuraava viikko aukeaa aina kun olet saanut vähintään 85% edeltävän viikon TMC-pisteistä. Tämän kurssin kautta **EI** ole mahdollista hakea opinto-oikeutta Helsingin Yliopistolle.

# Materiaali

Tehtyäsi kaikki asennustoimenpiteet ja rekisteröityäsi käyttäjätunnuksen TestMyCode -palveluun, voit jatkaa materiaalin ja aloittaa kurssin suorittamisen. Onnea kurssille!

<div class="actions">
    <a class="action" href="http://2015-ohjelmointi.mooc.fi/">Materiaaliin</a>
</div>

