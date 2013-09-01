# Inside Milan

![Mou icon](http://www.insidemilan.it/images/logo.png)

## Overview

**Inside Milan**, utlizza i datasets forniti dal portale *dati.comune.milano.it* presenti nella directory datasets.
L'applicativo è in grado di eseguire query in real-time su oltre 45000 record di metadati. E' possibile eseguire una ricerca di testo libero e di applicare dei filtri per zona.

### Indicizzazione dei dati

I dati forniti dal portale *dati.comune.milano.it* che sono stati utilizzati dall'applicativo sono di tipo shapefiles e dbf.
I dati geografici shapefiles sono stati convertiti nel formato geojson dove la parte di metadato è stata indicizzata insieme informazioni geografiche. Per i restanti dataset, dove non erano forniti i files di tipo shapefiles sono stati utilizzati i file di formato dbf.
Questo sottoinsieme di dati è risultato meno accurato con campi mancanti  in particolare la pare di geolocalizzazione. Per ovviare a questo problema sono state uilizzate le api **geocode** di Google, Bing per recuperare le coordinate del punto di interesse.
Nella directory **solr** è presene lo schema utilizzato dall'istanza solr utilizzata dall'apllicatico con la definizione dei tipo di campi e il nome dei campi di un metadato.
Nella directory **lib** sono presenti gli script in ruby per eseguire l'haversting dei dati in un file json utilizzato a sua volta come cache di solr.

### Server
Nella directory server è presente lo script che permette l'esecuzione di un server **Sinatra** il quale si occupa di fornire i layers utilizzati nell'applicativo (stazioni metro, piste ciclabili etc.).
Il server fornisce anche un metodo di interrogazione per verificare se esistono dei **twitts** a fronte di una query e una coordinata geospaziale.
Infine sono presenti anche il file di script per l'esecuzione su un server linux.

###Client
Il client si occupa di fornire l'interfaccia per l'utente finale, scritto interamente in javascritp. La basemap utilizzata è di openstreetmap.com . Sono stati utilizzati plugin esterni come ad esempio **ajax-solr** oppure **jquery**
