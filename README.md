# Aziz Ivan Gerard COULIBALY  

**Data Analyst | Business Analyst | Retail & Luxury Strategy**  
Allier stratégie, expérience terrain et analyse de données pour transformer les chiffres en leviers de décision.  

---

## À propos de moi  
Issu d’un parcours en stratégie d’entreprise (HEC Abidjan) et en marketing & management du luxe (ESGLUXE Paris), j’ai construit mon expertise sur le terrain (Baccarat, From Future) avant de me spécialiser dans l’analyse de données appliquée au commerce et à la performance retail.  

La conversion vers la data s’est imposée naturellement : comprendre les clients, piloter la performance et proposer des solutions concrètes nécessitent des outils analytiques puissants.  
Ce chemin m’a amené à maîtriser Excel avancé (TOSA), Power Query, Power Pivot, DAX, Power BI, ainsi que des notions de SQL.  

Mon portfolio GitHub illustre non seulement mes compétences techniques, mais aussi ma pédagogie et ma capacité à apprendre vite et appliquer sur des cas concrets.  

---

## Projets : Optimisation d’un reporting commercial avec Excel, Power Query & Power BI   
un fichier Excel non optimisé, multi-années, non exploitable pour le pilotage, l'analyse et la visualisation des indicateurs clés de performances.
##### Données brutes  
![Données brutes](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/5bd970744b8b89af5dc5cf5ed8c22d68de102cf4/Images/Capture%20Donne%CC%81e%20a%CC%80%20nettoyer.JPG)  
 

### Problème rencontré 
- Données dispersées sur plusieurs feuille et dans plusieurs dossiers
- Pas de Formatage des colonnes (dates, CA HT, ventes, Articles,  passages, Qte Remise, Remise HT, Qte Détaxe, Détaxe HT, Qte VAD, VAD ht, full prices, Qte Parfum, Parfum Ht, QteDiversificatio, Diversification HT)
- Pas de mise en forme conditionnel relative au weekend
- Pas de suivi dynamique d’une année à l’autre
- Calcul manuel des indicateurs : Panier moyen, Detaxe/CA, VAD/CA, Catégorie de produit (Full price, Parfum, Diversification)/CA par semaine/Mois/Année
  
  ---
  
  ### Étapes de traitement 
 **Power Query**  
- Nettoyage, homogénéisation et formatage des colonnes
  ##### Données nettoyées  
![Données nettoyées](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/f549ca6f097c08d514bdde162c7ac3a5cc0a4ffb/Images/Power%20query%20nettoyage.JPG) 

- Fusion des requêtes multi-mois : les classeurs possèdent 12 feuilles mensuelles. Après la fusion, le fichier obtenu est renommé "Données_ventesYYYY" chargé en tableau et rangé avec les autres années.
  ##### Fuision des requêtes multi-mois (2024, 2025, 2026, 2027, 2028, 2029, 2030)
![Fusion des requêtes multi-mois](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/99fd1f30b7feaaf1c4230377adb4a8ad338d57e7/Images/Capture%20fusion%20multi%20mois%202024.JPG)  

- Création d’un modèle anticipant les futures années : production d’un fichier Excel optimisé avec des tableaux permettant le calcul automatique des indicateurs,  
  ajout de nouvelles fonctionnalités (mise en forme conditionnelle des week-ends, filtre par semaine),  
  et anticipation des années à venir jusqu’en 2030
 ##### Modèle pour les années futurs
![Création d'un modèle optimisé pour les future année](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/03991317c3aec3d187def326df32d657871abba1/Images/Capture%20Fichier%20excel%20optimise%CC%81.JPG)   

- Normalisation des formats (dates, montants, devises)

  **Power BI**
  - Fusion des requêtes multi-année : après création, transformation et fusion multi-mois des classeurs annuels, je procède à la fusion multi-année des fichiers "Donnée_ventesYYYY"
  pour obtenir une table de faits unique centralisant toutes les ventes passées et futures 2024-2030, facilitant ainsi les calculs et l’application des mesures DAX
  ##### Fusion multi-année 
![Fusion multi-année](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/926448afcf6b1af7960da6077ce54d724682ca9a/Images/Capture%20Fusion%20multi%20anne%CC%81e.JPG) 

- Création d’une table calendrier (Date Table) afin de piloter le filtrage des données de ventes:
  `Calendar = ADDCOLUMNS(
    CALENDAR(DATE(2024,01,01),DATE(2030,12,01)),
"ANNEE",YEAR([Date]),
"SEMESTRE",IF(MONTH([Date])>=6,"S2","S1"))
`,
  ##### Table calendrier
  ![Table calendrier](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/934c277b09b2ed91d9f42bf637d1ebb11637d499/Images/Cre%CC%81ation%20table%20date.JPG)
  
- Modélisation des données de mise en relation : Dans notre cas la table de fait est la table regroupant toutes les données de ventes et la table de dimensions est la table date préalablement créé
   ##### Modèle de donnée
    ![Modélisation des donnée](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/bda5ddf721967d7f1d914379c57477efaae6d2ce/Images/Mode%CC%81lisation%20des%20donne%CC%81es.JPG)
  
- Mesures DAX :  
  - `CA = SUM(Donnée_vente[CAHT])`  
  - `CA N-1 = CALCULATE([CA], SAMEPERIODLASTYEAR(Calendar[Date]))` 
  - `Ecart = divide([CA] - [CA N-1],[CA N-1])`
  - `Panier moyen = divide([CA],sum(donnée_vente[ventes]))`
    ##### Mésures Calculées
 ![Mesures calculées](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/421cfade86bb3e96137bc9c5747c3a7eaea63c9f/Images/Capture%20mesures%20calcule%CC%81es.JPG) 
 
- Filtres dynamiques (année, mois) synchronisation des filtre, Page1,2,3 
- Visualisations : histogrammes combiné,  donut chart, Cartes 123, matrice, mise en forme conditionnel
  ##### Dashboard final  
![Dashboard final](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/b06d65daba868a85223704908908beed4d3eb5e0/Images/Capture%20Dashboard%20P1.JPG) 
![Dashboard final](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/36295d94e48934320758ba06b3ae60db067ceb8c/Images/Capture%20Dashboard%20Analyse%20comparative.JPG) 
![Dashboard final](https://github.com/azizivan2000-crypto/AZIZ-COULIBALY/blob/b06d65daba868a85223704908908beed4d3eb5e0/Images/Capture%20Dashboard%20P1.JPG) 

   ---
  
#### Résultats quantitatifs  
- Réduction du temps de rapport manuel de 1h30 à 20 minutes automatisées (gain de productivité de 78%)
- Fiabilité des données : 98%
- Adoption de l’outil par les équipes de ventes / manager au quotidien et lors des rapports mensuels à la hiérarchie

---

#### Résultats qualitatifs   
- Visualisations intuitives et interactive permettant à des non-techniciens de comprendre les performances en un coup d’œil 
- Renforcement de la confiance du manager dans les données utilisées au quotidien
- Suivi clair des écarts année N / N-1 ainsi que des indicateurs N/N-1

---

#### Résultats personnels  
- Acquisition de compétences clés en **Excel, Power Query avancé, PowerBI, DAX et modélisation relationnelle**  
- Développement d’une pédagogie pour vulgariser la donnée auprès d’équipes non techniques  
- Capacité à mener un projet complet, de l'observation terrain à un outil exploitable et adopté  
- Démonstration d’une capacité d'adaptation et d’apprentissage rapide 
- Amélioration de ma rigueur analytique et de ma capacité à transformer les chiffres en recommandations stratégiques
- Résilience face aux difficultés techniques par la recherche et l'expérimentation


[Voir un aperçu du dashboard](#docs/screenshot.png)  

---

## Compétences techniques  
- Analyse et visualisation : Excel Avancé (TOSA), Power Query, Power Pivot, DAX, Power BI  
- Gestion commerciale : SAP BO, Generix  
- Langages et data : notions SQL, DAX, modélisation relationnelle  
- Outils : Pack Office, Suite Google  



---

## Ce qui me différencie  

Je me distingue par ma capacité à apprendre rapidement et à appliquer mes compétences sur des projets concrets.  
Mon parcours combine une **vision 360°** (retail, stratégie, data) et une **pédagogie**, qui me permet d’expliquer des problématiques complexes de façon simple et accessible.  

Chaque projet est mené jusqu’au bout, avec des **livrables concrets**.  
Mon **esprit critique** me pousse à identifier les faiblesses des systèmes en place et à initier, à titre personnel, des solutions nouvelles.  
C’est pour moi une manière d’être **force de proposition**, de contribuer à l’amélioration de mon environnement de travail et de m’auto-challenger en permanence. 
Enfin, ma **curiosité et mon esprit d’investigation** me permettent de surmonter les obstacles techniques grâce à la recherche, à l’expérimentation et à la débrouillardise.   


---

## CV et contact  
- [Mon CV (PDF)](../CV%20aziz%20Coulibaly.pdf)  
- Email : [Azizivan2000@gmail.com](mailto:Azizivan2000@gmail.com)  
- Localisation : Île-de-France  
- LinkedIn : https://www.linkedin.com/in/coulibaly-aziz/

