# AI-Crypto-Price-Prediction

## Cerinta

Folosind datele istorice să se creeze un sistem de forecast pentru a estima prețul în funcție de setul de date utilizat (zi, oră, minut).
Procesarea seturilor de date și completarea lor cu Relative strength index, Moving average, si MACD.
Realizarea pentru fiecare set de date a unui model(de ex: SVM, RNN, LSTM, etc...) și testarea parametrilor de control ai modelelor în vederea îmbunătățirii performanței acestora
Includerea celor mai bune modele obținute într-o interfață grafică cu opțiuni de testare pe date reale (introduse manual) și posibilitatea alegerii manuale a intervalelor de timp pentru forecast.
(Optional) Integrarea unui API de culegere a datelor reale (ca de ex Bitcoin Price Index API) și testarea automată a aplicației pe acele date


## Ce am facut

* Am utilizat doua seturi de date pentru predictia pretului criptomonedei ETH: zi, ora.
* Am facut predictii utlizand diverse date:
  - utilizand doar pretul de inchidere
  - utilizand pretul de inchidere, RSI, SMA si MACD
  - utilizand secvente de forma (lungimea_secventei, 4), unde un element din secventa este de forma de mai sus
* Am facut diverse tipuri de predictii:
  - putem seta un offset pentru a determina cu cate zile in viitor vrem sa prezicem pretul utilizand informatiile curente din ziua/ora curenta
  - avand acest offset setat putem utiliza predictia ziuei de maine ca date de intrare in retea astfel incat sa obtinem predictia pretului de poimaine s.a.m.d
  - utilizand fiecare model am prezis pretul de astazi utilizand un offset de 1(folosind datele din ziua precedenta)
* Modele utilizate
  - un model linear
  - un model fully-connected(un model mai complex decat cel linear)
  - un model fully-connected-seq(similar cu lstm-ul acest model utilizeaza secvente)
  - LSTM
  - Prophet
  - ARIMA
* Parametri generali pentru modelele definite de noi(primele 5):
  - date testare: 0.2 din date
  - validation split: 0.2 din datele de antrenare
  - optimizzator: Adam
  - am utilizat checkpoint-uri pentru a pastra cel mai bun model obtinut pe parcursul antrenarii fiecarui model
  - am normalizat datele utilizand un MinMaxScaler
  
## Contributii
  * Alexandrescu Nicolae
    - modelul fully-connected-seq, actualizarea si modificarea codului care foloseste dataset-ul cu frecventa de o ora
  * Zaharia Andrei
    - modelul linear, normalizarea datelor
  * Urma Tudor irinel
    - modelul fully-connected, normalizarea datelor
  * Vacaru Robert
    - importarea datelor, adaugarea indicatorilor statistici si graficele cu date
  * Capatina Nicolae
    - LSTM, Prophet, ARIMA, grafice pentru evolutia modelelor si predictii, inversare normalizare, procesarea datelor, functiile de predictie, coordonarea echipei
