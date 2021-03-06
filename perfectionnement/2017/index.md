---
layout: page
title: Cours de Perfectionnement (2017)
---

---

## Trame

1. [Collecter des données sur le web](#scrape)
  * [a. Scraper le "cinéma" français](#cinema)
  * [b. Crawler et scraper les publications transparency](#transparency)
  * [c. Le casse-tête HackerNews](#hackernews)
2. [Insérer des données dans une BDD NoSQL](#nosql)
3. [Algorithmie et tests unitaires](#jaccard)
4. [Concevoir une recherche "full-text"](#fulltext)
5. [Développer une API REST et linter son code](#rest)
6. [Développer une app client pour visualiser les données](client)
  * [a. Utiliser webpack](#webpack)
  * [b. React + Redux](#reactredux)
  * [c. Le Hot Module Reload](#hmr)
  * [d. Les visualisation classiques](#viz)
  * [e. Utiliser D3 ou pas](#d3)
  * [f. Visualiser un réseau](#reseau)
7. [Détection de duplicats flous](#recordlinkage)
  * [a. Utiliser OpenRefine](#openrefine)
  * [b. Concevoir un algorithme de partitionnement](#clustering)
  * [c. MinHashing et partitionnement à l'échelle](#minhash)
8. [Les chaînes de Markov](#markov)
  * [a. Manipuler un réseau](#graph)
  * [b. Générer de fausses observations](#observations)
9. [Utiliser un algorithme de machine learning](#ml)

---

## Principes du cours

* Vous choisissez la granularité qui vous intéresse: vous pouvez très bien approfondir au maximum un seul des axes de la trame, ou au contraire tenter de travailler tous les axes
* Vous êtes libres de travailler les sujets dans n'importe quel sens, même si je vous recommande de suivre la trame qui se veut plus ou moins "logique" (et full-stack, tmtc).
* De la même manière, si vous souhaitez approfondir vraiment un domaine (le scraping, par exemple) et que les sujets proposés sont trop faciles, on peut tout à fait les corser.
* Vous êtes libres de constituer des équipes ou bien de travailler seul(e)s ou même de composer des ensembles flous. J'ai juste besoin d'avoir une idée globale de la géographie de ces ensembles pour pouvoir planifier.
* Si vous avez en tête des données plus concrètes et plus utiles pour vous que celles que je mets à disposition ou vous demande de récupérer, n'hésitez pas.
* Si vous avez des projets pédagogiques et personnels en rapport avec les sujets du cours et que vous voulez en profiter pour que nous puissions les travailler ensemble, allons-y (en *record linkage*, notamment).
* Si vous trouvez que la présente page n'est pas claire, discutons-en et ouvrons une fusiodemande. De plus, je vais probablement améliorer cette page au cours des deux journées au fur et à mesure que nous aborderons les différents sujets ensemble.
* De manière générale, il serait bon de publier votre code sur un repo Github. Notamment parce que cela vous entraîne à utiliser un outil de versionning et qu'il me sera plus facile de vous aider.
* Si vous avez des questions quand je ne suis pas là, ouvrez une issue sur le repo:

[Repo GitHub](https://github.com/Yomguithereal/courses)

---

## Langages

Vous êtes libres de travailler sur les langages de programmation que vous préférez.

Sachez seulement que je suis plus à même de vous aider sur des langages que je maîtrise (dans l'ordre):

* JavaScript / TypeScript etc.
* Python
* Clojure
* Ruby
* PHP
* Java
* C

---

## KickOff

!Aménagement horaire!

1. Composer la géographie des intérêts.
2. Planifier vos ambitions.
3. Faire des modules approfondis en fonction du plan.
4. Installer les dépendances lourdes nécessaires (scikit, jupyter, OpenRefine etc.).
5. 仕事!

---

<h3 id="scrape">1. Collecter des données sur le web</h3>

<h4 id="cinema">a. Scraper le "cinéma" français</h4>

URL: [http://www.cinema-francais.fr/](http://www.cinema-francais.fr/)

**Objectif**: récupérer une liste quelconque (monteurs, scénaristes etc.) et ensuite, si vous en avez envie, scraper une liste éclatée sur plusieurs pages.

**Difficultés**:

* Les données sales (trim, squeeze, parsing)

<h4 id="transparency">b. Crawler et scraper les publications transparency</h4>

URL: [https://www.transparency.org/whatwedo/publications](https://www.transparency.org/whatwedo/publications)

**Objectif**: récupérer la liste des publications ainsi que leurs métadonnées.

**Difficultés**:

* Throttling (le site est loin d'être rapide)
* Scheduling, fault-tolerance, queue, BDD
* Faire de la rétro-ingénierie sur une pagination pour la crawler.
* Scraper toutes les pages nécessaires afin de récupérer les données.

<h4 id="hackernews">c. Le casse-tête HackerNews</h4>

URL: [https://news.ycombinator.com/](https://news.ycombinator.com/)

**Objectif**: récupérer les données du site HackerNews.

**Difficultés**:

* Trouver des patterns dans du markup non-cohérent.

---

<h3 id="nosql">2. Insérer des données dans une BDD NoSQL</h3>

**Objectifs**:

1. Choisir une BDD NoSQL que vous souhaitez essayer (une qui soit pertinente et vous devrez justifier votre choix).
2. Y insérer les données que nous avons scrapé de transparency.org.
3. Etre capable de formuler des requêtes pour récupérer les données dont une API pourrait avoir besoin.

**Suggestions**:

* [MongoDB](https://docs.mongodb.com/)
* [Neo4j](https://neo4j.com/product/)
* [ElasticSearch](https://www.elastic.co/fr/products/elasticsearch)

[Lien](./projects/transparency/data.json) vers les données pour les feignant(e)s.

---

<h3 id="jaccard">3. Algorithmie et tests unitaires</h3>

**Objectifs**:

1. Implémenter un [index de Jaccard](https://en.wikipedia.org/wiki/Jaccard_index) (théorie des ensembles).
2. Ecrire des tests unitaires pour s'assurer de son bon fonctionnement (notion de régression).

**Suggestions**:

* (js) [mocha](https://mochajs.org/)
* (py) [unittest](https://docs.python.org/3/library/unittest.html)

---

<h3 id="fulltext">4. Concevoir une recherche "full-text"</h3>

**Objectifs**:

1. Créer un tokenizer
2. Trouver une liste de stopwords
3. Trouver ou créer un stemmer
4. Concevoir un index inversé
5. Requêter un index inversé
6. Ajouter un poil de logique floue
7. Pour les plus taré(e)s: Fréquences, taille, TF-IDF et similarité cosinus

[Lien](./projects/transparency/data.json) vers les données pour les feignant(e)s.

---

<h3 id="rest">5. Développer une API REST et linter son code</h3>

**Dépendances**: Il serait préférable d'avoir effectué les étapes précédentes ou afin de s'attaquer à cette partie dans la mesure où vous êtes censés avoir des données à servir.

**Objectif**:

1. Concevoir et développer une API REST (préférence MVC)
2. Linter son code afin de conserver un style cohérent

**Suggestions**:

* (js) [Express.js](http://expressjs.com/)
* (js) [Eslint](http://eslint.org/)
* (py) [Flask](http://flask.pocoo.org/)
* (py) [Pep8](https://pypi.python.org/pypi/pep8)

[Lien](./projects/transparency/data.json) vers les données pour les feignant(e)s.

---

<h3 id="client">6. Développer une app client pour visualiser les données</h3>

**Dépendances**: Il serait préférable d'avoir effectué les étapes précédentes.

**Astuce**: il vous est tout à fait possible de charger toutes les données en JSON depuis le client et utiliser un moteur de recherche côté client si vous ne voulez pas développer une API.

[Lien](./projects/transparency/data.json) vers les données pour les feignant(e)s.

<h4 id="webpack">a. Utiliser webpack</h4>

[https://webpack.js.org/](https://webpack.js.org/)

Utiliser le serveur de développement pour se faciliter la tâche.

<h4 id="reactredux">b. React + Redux</h4>

* [React](https://facebook.github.io/react/)
* [Redux](http://redux.js.org/)
  - La notion d'état centralisé et la programmation fonctionnelle
  - Constantes, reducers, actions
  - Créer un helper pour faire mieux que les `switch`
  - Les ducks
  - redux-thunk

<h4 id="hmr">c. Le Hot Module Reload</h4>

Configurer un HMR pour pouvoir développer confortablement et efficacement.

<h4 id="viz">d. Les visualisation classiques</h4>

**Objectifs**:

* Choisir comment représenter les données
* Utiliser [recharts](http://recharts.org/#/en-US/) pour afficher des visualisations simples.

<h4 id="d3">e. Utiliser D3 ou pas</h4>

* Comprendre la logique et l'intérêt de [d3](https://d3js.org/).
* Comprendre que sa couche de rendu est aujourd'hui peu utile.
* Mais que ses librairies annexes demeurent extrêmement utiles.

<h4 id="reseau">f. Visualiser un réseau</h4>

* Utiliser [sigma.js](http://sigmajs.org/) pour visualiser un réseau d'une certaine envergure.

---

<h3 id="recordlinkage">7. Détection de duplicats flous</h3>

<h4 id="openrefine">a. Utiliser OpenRefine</h4>

* [LibreOffice](https://fr.libreoffice.org/)
* [OpenRefine](http://openrefine.org/)

**Jeux de données**:

1. [Figshare](./resources/dirty-figshare.csv)
2. [Musicians](./resources/dirty-musicians.csv)
3. [Universities](./resources/dirty-universities.csv) (Ancien [TP]({{ site.baseurl }}/data/2016/tp/openrefine.html))

<h4 id="clustering">b. Concevoir un algorithme de partitionnement</h4>

1. Collision de clés
2. Algorithme quadratique naïf
3. Utilisation de structures de données dédiées (le Vantage Point Tree)

<h4 id="minhash">c. MinHashing et partitionnement à l'échelle</h4>

Pour les plus taré(e)s!

1. Les algorithmes de hash (le CRC32 notamment).
2. Principes du minhashing.
3. Préparer des documents textuels (page web, mail). 
4. Binning sur base de minhashing.

---

<h3 id="markov">8. Les chaînes de Markov</h3>

<h4 id="graph">a. Manipuler un réseau</h4>

Trouver une librairie ou concevoir un modèle de données pour manipuler des graphes à même de stocker des chaînes de Markov.

**Suggestions**:

* (js) [graphology](https://graphology.github.io/)
* (py) [networkx](https://networkx.readthedocs.io/en/stable/)

Trouver un moyen de sélectionner une valeur pondérée aléatoirement.

<h4 id="observations">b. Générer de fausses observations</h4>

* *Niveau 1*: Créer de faux mots du [dictionnaire](http://www.pallier.org/ressources/dicofr/dicofr.html).
* *Niveau 2*: Créer de faux produits du XIXe siècle ([products.csv](./resources/products.csv)).
* *Niveau 3*: Créer de faux cours d'HETIC (plus difficile, il faut trouver un syllabus).

---

<h3 id="ml">9. Utiliser un algorithme de machine learning</h3>

On va utiliser [scikit-learn](http://scikit-learn.org/stable/install.html).

Télécharger le dataset [ici](http://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#webspam).

Utiliser [Jupyter](http://jupyter.org/).

1. Trouver un cas d'usage (SPAM/HAM, par exemple).
2. Splitter le dataset.
3. Vectoriser le dataset.
4. Entraîner un modèle.
5. Evaluer la précision du modèle.
