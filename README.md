# Palo-Alto-Networks
# Github Repo: https://github.com/ErikFW/Palo-Alto-Networks
# File: Allow-Altibox.txt

Etter å ha oppdaget at Altibox app ikke lenger fungerer etter konfigurering av PANW NGFW, prøvde jeg å finne en løsning.
Det viser seg at Altibox appen kontakter et knippe med IP adresser for å initiere datastrømmen for den kanelen du vil se på.
Disse IP'ene er er ikke kategorisert og går dermed under kategorien "Unknown". 

I min brannmur så er Kategorien unknown satt til Block av sikkerhetsgrunner.

Løsningen ble å lage en unntaks regel for Altibox appen som tillater trafikk fra de IP'ene det gjelder.

Jeg har satt opp et filter i loggene for å fange de IPene som blir stoppet og legger disse inn i regelen.

Denne listen er eksportert ut og er tilgjengelig her på Github 

## Hvordan sette opp regelen ##

I din Palo Alto brannmur, gå til Object - Custom OBjects - URL Category
Klikk Add nederst i bildet
I dialogboksen som dukker opp fyller du inn følgende
Name: Allow-Altibox
Description: Allow list for å få altibox app til å fungere.
Type: URL List

Klikk så import og importer Allow-Altibox.txt filer du laster ned herifra

klikk OK og commit endringen
