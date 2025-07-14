---
title: Veelgestelde vragen over het bijgewerkte levenscyclusbeleid voor Adobe Commerce-releases
description: 'Adobe Commerce biedt kwaliteitsoplossingen voor een kleine release gedurende minimaal 12 maanden vanaf de algemene beschikbaarheidsdatum van de volgende secundaire softwarerelease. De manier waarop wij in deze periode kwaliteitscorrecties aanbrengen, is aan het veranderen:'
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: f11596ea844fead42141c7e1fea586b2a11f757a
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---

# Veelgestelde vragen over het bijgewerkte levenscyclusbeleid voor Adobe Commerce-releases

## Wat verandert er?

Adobe Commerce biedt kwaliteitsoplossingen voor een kleine release gedurende minimaal 12 maanden vanaf de algemene beschikbaarheidsdatum van de volgende secundaire softwarerelease. De manier waarop wij in deze periode kwaliteitscorrecties aanbrengen, is aan het veranderen:

* **Voorafgaand beleid:** momenteel bevestigt de kwaliteit aan de vorige lijn die in het venster van 12 maanden EOS is door onze driemaandelijkse flardversie wordt geleverd, vandaar het maken van de driemaandelijkse flarden een combinatie veiligheid + kwaliteit.
* **Nieuw beleid:** Beginnend met 2.4 als huidigste minder belangrijke versielijn, de flarden van de versie voor de vorige gesteunde lijn (2.3) zullen zich aan veiligheid-slechts bewegen. Wij zullen nog kwaliteitsmoeilijke situaties voor de vorige gesteunde lijn tijdens het 12 maandenvenster na versie van een minder belangrijk (als 2.4) en verdere nieuwe minder belangrijke versielijnen leveren; maar die zullen door [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) beschikbaar worden gemaakt en slechts op kritieke kwesties worden geconcentreerd.

## Wanneer wordt dit beleid van kracht?

Adobe Commerce 2.3.6 zal naar verwachting op 15 oktober 2020 worden uitgebracht en zal naar verwachting de laatste patchrelease voor Adobe Commerce 2.3 zijn die zowel kwaliteit + beveiliging omvat. Na 2.3.6, zal 2.3.x lijn veiligheid-slechts worden en kritieke kwaliteitskwesties voor 2.3 kunnen via QPT worden opgelost.

>[!NOTE]
>
>De enige keer dat we een volledige versie van 2.3 uitbrengen, is of we onze technologiestapel moeten handhaven, zoals voor PHP of Elasticsearch. Dit gebeurt in het tweede kwartaal van 2021 met een verplichte update van PHP 7.4. We verhogen de lijn naar 2.3.7. Voor details, verwijs naar [ PHP 7.4 steun voor Adobe Commerce 2.3.x versielijn ](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog post.

## Wat is een veiligheid-slechts versie?

Beveiligingsreleases bevatten alleen beveiligingsoplossingen en er is geen kwaliteit hersteld. Houd er echter rekening mee dat onze beveiligingsupdates specifieke hotfixes kunnen bevatten wanneer we deze absoluut essentieel achten om Adobe Commerce uit te voeren.

## Zal er nog een beveiligingsuitgave zijn voor de laatste regel (vanaf de publicatie, 2.4)?

Adobe zal ook voor de meest recente releaselijn alleen nog maar beveiligingsreleases hebben. Het proces voor deze wordt geschetst in [ Introducerend de Nieuwe veiligheid-slechts post DevBlog van de Versie van het Patch ](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287).

## Wat is het gereedschap Kwaliteitspatches?

Gelieve te verwijzen naar het [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in onze steunkennisbasis zelf-te dienen.

## Wie zou dit nieuwe beleid moeten gebruiken?

Het nieuwe beleid is bedoeld om handelsagenten in staat te stellen strategisch plannen te maken voor de jaarlijkse ontwikkelingskosten van Adobe Commerce, terwijl ze tegelijkertijd de veiligheid en kritieke kwaliteit tijdens deze strategische cycli kunnen behouden. Het kan ook worden gebruikt door handelaren die om veiligheid over alles geven en over het algemeen gelukkig zijn met de stabiliteit van oudere, gesteunde lijn. Merchants vinden het misschien gemakkelijker om voor deze verbeteringen te plannen en te begroten aangezien zij voorspelbaarder zullen zijn.

## Moet Merchants nog steeds upgraden naar de laatste regel?

Uiteindelijk moeten alle handelaren prioriteit geven aan de planning om de nieuwste Adobe Commerce-lijn tijdig aan te nemen. De nieuwe lijn van de Veiligheid slechts en het hulpmiddel QPT zijn niet bedoeld om de strategische verbeteringsroadmap voor verkopers te vervangen; eerder, bieden zij flexibiliteit voor verkopers in het plannen van hun verbeteringsroadmap en een middel om snel op veiligheid/kwaliteitskwesties te reageren zonder het moeten een volledige verbetering uitvoeren.

## Hoe zal ik kwaliteitsmoeilijke situaties op gesteunde minder belangrijke versies krijgen die niet de recentste lijn zijn?

De moeilijke situaties zullen beschikbaar via het [ Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) worden gemaakt.

## Hoe krijg ik correcties voor kwaliteit op de meest recente regel?

De huidige regel zal kwaliteit hebben als onderdeel van de driemaandelijkse actualisering. Als u tussen releases contact opneemt met ondersteuning voor een oplossing op de meest recente regel, wordt deze geleverd via QPT. Als u vervolgens een upgrade uitvoert naar de release die deze oplossing bevat, wordt deze toegepast via de driemaandelijkse patch.

## Welk soort kwaliteitskwesties zal op gesteunde minder belangrijke versies worden opgelost die niet de recentste lijn zijn?

Alleen belangrijke kwaliteitsproblemen die kernstromen onderbreken, worden in de vorige regel (2.3) opgelost en via QPT geleverd.

## Zullen eventuele kwaliteitscorrecties deel uitmaken van de driemaandelijkse versie van ondersteunde kleine versies die niet de laatste regel zijn?

Ja, als onderdeel van de beveiligings-enige lijn, geven wij wat Adobe &quot;hete moeilijke situaties&quot;aan die lijn noemt vrij, zijn dit hoogst kritieke kwesties die de toepassing van Adobe Commerce beïnvloeden.

## Zullen de veiligheidsverbeteringen en het QPT tezelfdertijd worden geleverd?

Op de regel met alleen zekerheid wordt het driemaandelijkse releaseschema gevolgd en wordt de code -p1 vrijgegeven. Voorbeeld 2.3.6-p1. Kwaliteit wordt ad hoc vrijgegeven omdat kwaliteitsproblemen worden ontdekt en opgelost en deze beschikbaar worden gesteld via QPT.

## Wat doe ik als ik een kwaliteitsprobleem heb dat niet wordt opgelost in ondersteunde kleine versies die niet de nieuwste regel of QPT zijn?

De vorige lijn die veiligheid-slechts is betekent het belangrijkste voordeel blijft veilig. Alleen patches voor belangrijke problemen die kernstromen doorbreken, worden beschikbaar gesteld via QPT.

Kwesties die geen invloed hebben op kernstromen of die een tijdelijke oplossing hebben, worden alleen op de meest recente regel opgelost. Adobe moedigt degenen die zowel kritische als niet-kritische oplossingen willen, aan om naar de meest recente lijn te gaan.

## Zijn upgrades duurder of moeilijker voor Merchants als ze alleen op de beveiligings-regel blijven staan totdat het einde van de ondersteuning voor beveiliging is bereikt?

In theorie moeten de kosten voor de Merchant gelijk zijn in termen van ontwikkelingstijden, zolang zij geen groot aantal kwaliteitspatches hebben aangenomen. Als een Merchant vindt dat zij meer dan een paar flarden via het hulpmiddel van QPT nodig hebben of willen, is de aanbeveling dat zij aan een verbetering aan de recentste versie van Adobe Commerce voorrang geven. Als u een groot aantal kwaliteitspatches aanneemt, in plaats van de huidige versie van Adobe Commerce, kunnen de ontwikkelingskosten en de complexiteit van de upgrade toenemen zodra de beveiligings-enige lijn het einde van de ondersteuning bereikt.

## Waarom zou ik de hoeveelheid kwaliteitspatches die via QPT worden geleverd, moeten beperken?

Door het toepassen van vele individuele kwaliteitsmoeilijke situaties maakt u uw code van Adobe Commerce complexer. De toegevoegde complexiteit kan leiden tot onvoorspelbare wijzigingen bij de upgrade naar de meest recente releaselijn. Daarom raden wij aan om het QPT spaarzaam en alleen voor de meest kritische correcties te gebruiken.

## En hoe zit het met de naleving van technische stapels?

Tijdens de levensduur van een releaselijn zijn er updates voor verschillende technologiestapels zoals PHP of Elasticsearch die moeten worden bijgewerkt om compatibel te blijven. We zullen onze handelaren zo veel mogelijk op de hoogte stellen van het feit dat deze komen.

Opmerking: in het tweede kwartaal van 2021 moeten PHP en Redis op de 2.3.x regel worden bijgewerkt om compatibel te blijven. Hierdoor wordt de lijn tot 2.3.7 verhoogd. Voor details, verwijs naar [ PHP 7.4 steun voor Adobe Commerce 2.3.x versielijn ](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog post.
