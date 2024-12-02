---
title: Problemen met de eCommerce-omzet in Google opsporen
description: 'Dit artikel biedt oplossingen voor verschillen tussen Google en Magento Business Intelligence (MBI). Het volgen van de eCommerce van Google brengt macht aan zowel uw rekening van Googles Analytics als uw dashboards MBI, maar het resulteert in vele cliënten die ons vragen: Moeten beide hulpmiddelen het zelfde bedrag van **orders* en **opbrengst** melden?'
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Problemen met de eCommerce-omzet in Google opsporen

Dit artikel biedt oplossingen voor verschillen tussen Google en Magento Business Intelligence (MBI). Het volgen van de eCommerce van Google brengt macht aan zowel uw rekening van Googles Analytics als uw dashboards MBI, maar het resulteert in vele cliënten die ons vragen: Moeten beide hulpmiddelen het zelfde bedrag van **orden** en **opbrengst** melden?

In onze ervaring is het antwoord in bijna alle gevallen &quot;nee&quot;. De reden hiervoor is dat de eCommerce-tracering van Google de bestelgegevens verkrijgt tijdens een klikgebeurtenis op uw website, die veel orderkenmerken mist die later in de database worden vastgelegd - alles van bestellingen die niet zijn geregistreerd tot bestellingen die later worden geannuleerd of terugbetaald.

We weten dat een discrepantie tussen Google en MBI onzekerheid kan veroorzaken voor u en uw team. We willen u helpen het verschil tussen deze twee getallen te begrijpen. Hierdoor kunnen aanpassingen in uw Google-account of -database zichtbaar worden.

## Waarom rapporteert GA **minder** opbrengst dan mijn gegevensbestand?

Als Googles Analytics opdrachten en inkomsten onderschrijven, geeft dit aan dat niet alle orders die op uw site worden geplaatst, worden vastgelegd. Aangezien u weet dat uw databasegegevens het definitieve nummer zijn, kunt u een aantal stappen nemen om te proberen de hoofdoorzaak te bepalen - en Google mogelijk helpen meer informatie vast te leggen.

* Je hebt Google eCommerce tracking niet altijd ingeschakeld. Kijk eens naar een kleinere, recentere periode.
* Uw Google eCommerce-tracking is niet ingesteld om aankopen van bepaalde browsers, besturingssystemen of apparaten vast te leggen.
* De klikgebeurtenis die bij je eCommerce in Google hoort, houdt de belasting, verzending of andere kosten boven het totaalbedrag van de bestelling niet correct bij.
* De tijdstempel van de database bevindt zich in een andere tijdzone dan de tijdstempel van uw Googles Analytics.
* Mensen kunnen uw site bezoeken via incognitovensters of met uitgezette cookies.

## Waarom rapporteert GA **meer** opbrengst dan mijn gegevensbestand?

We hebben ontdekt dat het vaker voorkomt dat Googles Analytics bestellingen en inkomsten te veel rapporteren in vergelijking met een eCommerce-database. Dit is niet altijd slecht. Uw database is het definitieve overzicht van de transacties die op uw website zijn uitgevoerd. Er zijn verschillende redenen waarom Google een hoge melding kan maken, zelfs als u deze perfect hebt ingesteld:

* eCommerce-tracking vangt dubbele knopklikken vast en registreert alleen als een enkele volgorde in uw database.
* U hebt een groot aantal geannuleerde, terugbetaalde of gefraudeerde bestellingen. Dit is een statuswijziging die plaatsvindt nadat eCommerce de gegevens bijhoudt.
* Uw **Inkomsten** en **Orders** metriek sluiten opzettelijk test of interne orden uit, die Google niet kan onderscheiden.
* Bestellingen kunnen onder bepaalde omstandigheden niet in uw database worden geplaatst.
* Het volgen van eCommerce in Google is niet op de hoogte van coupons en kortingen op de bestelling.
* De tijdstempel van de database bevindt zich in een andere tijdzone dan de tijdstempel van uw Googles Analytics.

Houd er rekening mee dat zelfs als Google een hoger aantal rapporteert dan uw database, sommige bestellingen waarschijnlijk nog ontbreken om de redenen die in de bovenstaande sectie worden beschreven.

## Problemen oplossen

* Creeer een kloon van uw **metrische Inkomsten** zonder filters die het resultaat beperken. De filters Bestellingen tellen of Klanten tellen zijn belangrijk, maar Google heeft geen equivalent filter.
* Bekijk een kleine recente periode, zoals een paar uur eerder deze week.
* Zodra u Google eCommerce het volgen opstelling in MBI hebt, gebruik Filter of groep-door om één enkele Source, Medium, of Campagne te controleren. Doe dan hetzelfde in Google. Een bron met minder verkeer/opbrengst zal beter zijn, aangezien het als minder marge voor fout is te hebben.
