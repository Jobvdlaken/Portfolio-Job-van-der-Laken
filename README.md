# Portfolio-Job-van-der-Laken

## Inhoudsopgave:

#### Datacamp certificaten

- [Datacamp](#datacamp)

#### Analyses

- [Predictive analysis](#predictive-analysis)

#### Domein kennis 

- [Domain knowledge](#domain-knowledge)

#### Data voorbereiden

- [Data preprocessing](#data-preprocessing)

#### Communicatie

- [Communication](#communication)

#### Literatuur
- [Bronnen](#bronnen)

## Datacamp
Tijdens de minor heb ik gewerkt aan mijn Datacamp opdrachten. De certificaten van de behaalde cursussen staan hieronder weergegeven. 

![image](https://user-images.githubusercontent.com/120382552/211587932-549f9ec4-e7a7-4952-a514-21c0f8d538df.png)
![image](https://user-images.githubusercontent.com/120382552/211588473-abae4d75-32b6-4ee7-9764-1b9319d5e208.png)
![image](https://user-images.githubusercontent.com/120382552/211588788-9ad885c2-5698-4cfe-9b5c-543f7b830e16.png)
![image](https://user-images.githubusercontent.com/120382552/211588929-8d4aa4d8-cb65-4b05-bda1-9d100c3fc042.png)
![image](https://user-images.githubusercontent.com/120382552/211589154-129b4b0d-ca04-40a5-9cf8-32407cc5dbd5.png)
![image](https://user-images.githubusercontent.com/120382552/211589595-95c507a0-6776-4e16-808a-ce6f88bd2202.png)
![image](https://user-images.githubusercontent.com/120382552/211589834-4511120f-28be-4cff-8d00-8e87ba360880.png)
![image](https://user-images.githubusercontent.com/120382552/211589995-96cf907f-fac7-4df3-980f-0eaebf37e23c.png)
![image](https://user-images.githubusercontent.com/120382552/211594788-dca6c8be-edfd-4a47-b038-1b3ebeff5249.png)
![image](https://user-images.githubusercontent.com/120382552/211595022-cd79343a-1ced-407d-a89f-d263fc9ee545.png)
![image](https://user-images.githubusercontent.com/120382552/211595169-91c943fa-6d1c-4da7-a156-02f1645fbbac.png)
![image](https://user-images.githubusercontent.com/120382552/211595304-e4aacd8a-0a87-4422-99cb-a9348504c2cc.png)
![image](https://user-images.githubusercontent.com/120382552/211595437-ab3b0c90-67ea-401c-8673-b8d36a8c766b.png)
![image](https://user-images.githubusercontent.com/120382552/211595563-0a508d2b-4852-4af1-8809-549b5b439361.png)
![image](https://user-images.githubusercontent.com/120382552/211595704-f6eba98e-30fb-4a8e-8e48-d6a52351d376.png)


## Predictive analysis
Hieronder staan de modellen waar ik het meest mee gewerkt heb tijdens de minor. RFC&DTC zijn de Random Forest Classifier en de DecisionTree Classifier, die zijn gebruikt voor het foodboost project. Daarna komen Polynomial Feautres en LSTM. Deze zijn gebruikt voor het energieproject.

Voor het foodboost project is er als eerst geoefend met een kleinere dataset. In deze dataset zaten alleen de gerechten van Jamie Oliver en de Oost-europese gerechten.
Het was de bedoeling om op basis van iemands zes lievelings gerechten (Jamie Oliver of Oos-europees) te bepalen of zij het gerecht gemengde geroosterde groenten wel of niet lekker vinden. Dit is een calssificatie probleem. Het gaat hier namelijk om het wel of niet lekker vinden van een gerecht, ookwel een 1 (wel) of een 0 (niet). Om deze reden heb ik twee classifiers toegepast, Random Forest en de DecisionTree. 

In [Data preprocessing](#data-preprocessing) staat uitgelegd hoe de data is voorbereid voor alle modellen. 

Om de modellen te evalueren is onder andere gebruik gemaakt van de accuracy, precision en recall. Dit zijn evaluatiemetrieken voor classificatieproblemen. Vooral door middel van de lessen van de minor en het een en ander zoeken op internet, heb ik geleerd hoe je classificatie modellen moet toepassen en evalueren. In het document staan de uitkomsten van de evaluatiemetrieken. Deze scores wil je zo hoog mogelijk hebben. Hierbij betekent een hoge accuracy dat het model veel goede voorspellingen heeft gedaan, een hoge precision betekent dat er vooral weinig false positvies zijn voorspelt en een hoge recall betekent dat er vooral weinig false negatives zijn voorspelt. Ook is er gebruik gemaakt van een receiver operating characteristic curve (ROC curve) in combinatie met de area under curve (AUC). Op deze manier kan je duidelijk zien welk model beter presteerd door middel van een plot. Des te groter de AUC score, des te beter het model. De scores zijn uiteindelijk best wel hoog, wat te verwachten was, omdat er bij het maken van de simulatie aan is gedacht om iemand alleen Jamie Oliver of alleen Oost-europese gerechten te geven.

Uiteindelijk was het doel in dit project om de dataset uit te breiden en een zo hoog mogelijke precision te genereren, zo voorspel je bijna niet dat een persoon een gerecht wel lekker vindt, maar in werkelijkheid helemaal niet.

- [RFC&DTC](RFC&DTC2.ipynb)

Aan het begin van het energieproject heb ik eerst geprobeerd om een voorspellend model te maken, voor het energieverbruik per dag, met Polynomiale Regeressie. Bij het voorspellen van energieverbruik over tijd komt tijdreeksdata kijken, dit is een vorm van regressie. Daarom dacht ik dat Polynomiale Regressie kon gaan werken (dit is dus verder niet op literatuur gebaseerd). Toen ik ging zoeken naar informatie om dit toe te passen, kwam ik vaak het principe Polynomial Features tegen. Hier worden namelijk, met de features die mee worden gegeven, nieuwe interactietermen gegenereerd. Op deze manier dacht ik mogelijk nieuwe verbanden te kunnen vinden, wat uiteindelijk kon leiden tot betere voorspellingen. De features die zijn meegegeven: de dag van het jaar en 4 dummyvariabelen van welk seizoen het is. 

Om Polynomiale Regressie te evalueren is de R2 score gebruikt. Ik heb voor deze evaluatiemetriek gekozen, omdat ik te maken heb met een regressieprobleem en de R2 score dan ook vaak wordt gebruikt voor regressiemodellen. Aan het begin kwam de R2 score ontzettend laag uit (veel lager dan 0), wat betekent dat het model slecht presteert. Ik heb daarom de outliers uit de dataset gehaald, hoe dit is gedaan staat in [Data preprocessing](#data-preprocessing).

Na het verwijderen van de outliers en het maken van de voorspelling, kwam er alsnog een lage R2 uit, omdat Polynomiale Regressie met veel degrees soms onrealistische pieken of dalen voorspelt. Om deze reden heb ik het aantal degrees laag gezet en als er een zo'n waarde voorspelt werd, heb ik deze vervangen voor een voorspelling van de dag ervoor. Door deze aanpassingen waren de R2 scores van sommige huisjes een stuk beter geworden (hoger dan 0.5). 

Ik ben mij ervan bewust dat dit veel gesleutel is aan het model, zeker het laatste gedeelte met het vervangen van onrealistische voorspellingen. Dit hebben wij als groep onder andere daarom ook niet gebruikt voor het verslag. Desalniettemin heb ik hier wel van kunnen leren hoe je Polynomiale Regressie kan toepassen in combinatie met Polynomial Features, maar dat dit misschien niet de goede optie is voor deze data. 

- [Polynomial Features](PolyF.ipynb)

Uiteindelijk heb ik Long Short Term Memory (LSTM) toegepast om het energieverbruik per dag proberen te voorspellen. In een studie uit 2020 werd LSTM ook toegepast voor het voorspellen van energeiverbruik, waaruit bleek dat LSTM een grote potentie heeft om goede voorspellingen te maken op energieverbruik data (Wang, 2020). Een studie uit 2019 paste een CNN-LSTM toe om energieverbruik te voorspellen, zij stelde CNN-LSTM voor voor een robuuste en efficiënte voorspelling (Kim, 2019). 

LSTM's werken goed op sequentiële data als energieverbruik over tijd, omdat er tijdens het maken van een voorspelling rekening wordt gehouden met voorgaande inputs, anders dan het individueel behandelen van elke input. Het toepassen heb ik eerst gedaan met Tensorflow, maar hierdoor ging de server erg vastlopen, waarna ik PyTorch heb gebruikt. Ik heb veel op het internet gezocht naar hoe ik PyTorch moest gebruiken om het model te maken. Daardoor wist ik hoe de LSTM klasse in elkaar zit en heb ik deze zelf nagemaakt. Hoe de data voor LSTM is voorbereid staat in [Data preprocessing](#data-preprocessing). 

Het trainen is gedaan met 100 epochs en een hidden size van 35. Dit is niet heel veel, maar met meer epochs en een grotere hiddensize, ging het model heel erg overfitten op de trainingsdata. Nadat de voorspelling is gemaakt op de stationaire data, is dit eerst terug gezet naar het voorspelde energieverbruik om dit met het echte verbruik te vergelijken. Voor het evalueren van het model zijn verschillende scores gebruikt. De MSE, RMSE en MAE kwamen vooral vaak in de literatuur voor als evalutatiemetrieken. Daarnaast is ook de R2 score weer gebruikt omdat deze goed past bij het evalueren van regressiemodellen. 

De voorspelling zijn gemaakt voor huisje 26, omdat deze een verloop had zonder onverwachte pieken of dalen over het jaar. In de winter werd veel energie verbruikt en in de zomer weinig. De R2 score die uit dit model kwam was 0.26 wat misschien erg laag lijkt, maar in vergelijking met de andere huisjes is het nog best hoog. Dit was te zien aan de gemiddelde R2 score van alle huishoudens.

De gemiddelde scores van alle huisjes zijn berekend en de R2 scores zijn overzichtelijk geplot, zodat dit gebruikt kon worden in het verslag.

- [LSTM](LSTMgoed.ipynb)

## Domain knowledge

Om de modellen die zijn toegepast in het energie project voor onszelf beter te begrijpen, heeft iedereen in het groepje zijn/haar model in eigen woorden proberen uit te leggen. Ik heb dit gedaan voor het LSTM model. De informatie heb ik gevonden in zowel de literatuur (referentie staat in het document) als op het internet. Op deze manier heb ik mijn domein kennis weten te vergroten over LSTM's.  

Om mijn domein kennis, naast de lessen van de minor, te vergroten heb ik ook veel geleerd van Josh Starmer van het YouTube kanaal StatQuest. Hier staan veel video's op over de basis gedachten achter de machine learning modellen. Ik had tijdens de minor veel interesse in hoe de modellen echt werken. Onder andere de video's hebben mij goed geholpen om een basis idee te krijgen van de wiskunde achter bijvoorbeeld neurale netwerken en LSTM's.

Hieronder staat de link naar de tekst waarin ik geprobeerd heb om alles wat ik heb geleerd over LSTM uit te leggen. 
- [LSTM uitleg](LSTMtxt.pdf)

## Data preprocessing

Voor het foodboost project is een simulatie van gebruikers gemaakt die zeven lievelings gerechten hadden van Jamie Oliver of van Oost-europese gerechten. Dit is gedaan aan de hand van de twee tags. Er is gekozen voor deze twee, omdat er bij beide niet al te veel gerechten bij hoorde en zij ook evenveel gerechten in de lijst hadden. Het was namelijk de bedoeling om een soort verband te creeëren, zodat het model niet voorspelt dat iemand een Oost-europees gerecht lekker vindt als diegene alleen van de Jamie Oliver gerechten houdt. Op deze manier hebben wij als projectgroep geoefend met de verschillende classificatie modellen. In onderstaand document is te zien hoe de simulatie is gemaakt.

- [Simulatie Foodboost](SimulatieJ&O.ipynb)

Het voorbereiden van de data uit de simulatie van Jamie Oliver en Oost-europese gerechten, is gedaan met de train_test_split functie. Deze functie verdeeld de data in train- en testdata. Ik heb gekozen voor een train size van 80% en en testsize van 20%. Daarna heb ik een beetje geoefend met RandomizedSearchCV om de hyperparemters te tunen voor het Random Forest model. 

- [RFC&DTC](RFC&DTC2.ipynb)

Voor Polynomiale Regressie zijn 5 features gebruikt, de dag van het jaar en 4 dummyvariabelen van welk seizoen het is in het jaar. Voor de eerste feature is er een range van 365 getallen toegevoegd aan het dataframe, zodat de getallen per rij oplopen. Daarna is er een functie gemaakt die op basis van de dagen in het jaar een 1 (wel) of een 0 (niet) neerzet afhankelijk van welk seizoen het is. 

De target variabele was in dit geval het energieverbruik per dag en hiervan zijn de outliers eruit gehaald. Dit is gedaan met het gemiddelde en de standaarddeviatie per seizoen. Als een waarde meer dan 3 standaarddeviaties afwijkt van het gemiddelde, dan wordt deze vervangen met het energeiverbruik van de dag ervoor. In onderstaand document RFC&DTC is de functie add_season en verwijder_outlier te zien. 
- [Polynomial Features](PolyF.ipynb)

Om LSTM toe te passen op de data, is als eerst de data stationair gemaakt. Op deze manier veranderd het gemiddelde en de standaarddeviatie van de data niet over tijd, waardoor het model beter kan leren. De stationaire data is in de funtie df_to_X_y gestopt om een dataframe te maken. Zo is als feature het energieverbruik van elke dag in één hele week (7 dagen) gebruikt, waarbij de volgende dag na deze week de target variabele is. De data is daarna gesplist in de eerste 10 maanden als traindata en de laatste 2 maanden als testdata. Dan is het nog belangrijk dat de features en target variabele worden omgezet naar Torch variabelen om gebruik te maken van PyTorch.
In onderstaand document bij het kopje 'Voorbereiden van data' is te zien hoe dit is gedaan.
- [LSTM](LSTMgoed.ipynb)

## Communication
Binnen de minor vonden er ook af en toe presentaties plaats over de voortgang van het project. Ik heb zowel interne als externe presentaties gegeven. De twee externe presentaties waarbij ik onder andere spreker was, staan hieronder gelinkt. De eind presentatie van het Food Boost project deed ik samen met Sjoerd en de 2e externe presentatie van het energie project, deed ik met Senna en Sjoerd. Daarnaast heb ik ook veel interne presentaties gegeven, af en toe met een van de groepsgenoten en af en toe alleen.

- [Food Boost externe presentatie](FoodBoostEindpresentatie.pptx)
- [Energie project externe presentatie 2](Energy2.pptx)

Voor het verslag heb ik het deel van de LSTM uitgelegd met de resultaten en de bijbehorende analyse. Daarnaast heb ik ook het deel evalueren in de methode en de conclusie geschreven.

## Bronnen 


Kim, T. Y., & Cho, S. B. (2019). Predicting residential energy consumption using CNN-LSTM neural networks. Energy, 182, 72-81. 

Wang, J. Q., Du, Y., & Wang, J. (2020). LSTM based long-term energy consumption prediction with periodicity. Energy, 197, 117197. 
