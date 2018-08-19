# Potree

## Nous tempérons les îlots de chaleur des grandes villes du Québec en plantant des arbres !

### Nous encourageons la plantation de davantage d'arbres en milieu urbain, pour lutter contre les effets néfastes des îlots de chaleur. Nous rassemblons les opinions des citoyens sur la végétation de leur quartier, et leur permettons de contribuer au recensement des arbres de la municipalité.

[Jeu de données des arbres de Montréal](https://www.donneesquebec.ca/recherche/fr/dataset/vmtl-arbres/resource/c6c5afe8-10be-4539-8eae-93918ea9866e#avertissementTelechargement_Inventairearbrespublics-Fichierconsolid%C3%A9(Arrondissementsdanslesyst%C3%A8mecorporatifseulement))

[Jeu de données sur les arbres de Québec](https://www.donneesquebec.ca/recherche/fr/dataset/vque_26/resource/13a51853-a5b5-4add-8791-02ccba5c1be7?view_id=6aa48ec4-e6d7-40d4-9660-d938be4b3c03#close)

[Jeu de données sur les arbres de Repentigny](https://www.donneesquebec.ca/recherche/fr/dataset/vrep-arbres/resource/0ab4da5a-b470-4774-9f2a-4d9bb19763a5#avertissementTelechargement_Arbres)

[Données provinciales sur les îlots de chaleur](https://www.donneesquebec.ca/recherche/fr/dataset/ilots-de-chaleur-fraicheur-urbains-et-temperature-de-surface)


## some deploy instructions

https://github.com/ogrergo/hackqc2018

## Tree database (mongoDB)
### drop
    mongo
    > show dbs
    > use hackqc-2018
    > db.dropDatabase()

### repopulate
This takes a couple minutes

    cd data && ./get_data.sh && cd ..
    python3 init_db.py -c mtl
    python3 init_db.py -c qc
    python3 init_db.py -c rep
    python3 make_exemples.py


## Starting the server
edit `demo/js/bundle.js`, change `SERVER_URL` (around line 38687)

Run with `gunicorn --access-logfile access_log --error-logfile error_log -b 127.0.0.1:5000 app.api:app`


### statics
    cp -r hackqc2018/demo/* /var/www/potree/

To rebuild the `bundle.js` file, run `browserify src/main.js > bundle.js`
