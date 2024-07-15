---
title: 'ACSD-49389: klaar voor het ophalen van e-mail verzonden door API wanneer niet gereed voor ophalen'
description: Pas de ACSD-49389-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de API een e-mailbericht verstuurt dat gereed is voor ophalen wanneer de bestelling niet klaar is voor ophalen.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: klaar voor het ophalen van e-mail verzonden door API wanneer niet klaar voor ophalen

De ACSD-49389-patch verhelpt het probleem dat een e-mailbericht met de functie &quot;ready-for-pickup&quot; wordt verzonden door de API wanneer de bestelling niet klaar is voor ophalen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49389. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren als het flard met uw versie van Adobe Commerce compatibel is, werk het `magento/quality-patches` pakket aan de recentste versie bij en controleer de verenigbaarheid op de [ QPT landende pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De API stuurt een e-mailbericht dat u kunt ophalen wanneer de bestelling nog niet klaar is om te worden opgehaald.

<u> Stappen om </u> te reproduceren:

1. Schakel de methode *[!UICONTROL In-Store Delivery]* in.
1. Maak een aandelenbron met de ophaallocatie ingeschakeld.
1. Maak nieuwe voorraad met behulp van de hoofdwebsite met de hierboven gemaakte bron.
1. Maak een product dat dezelfde bron toewijst.
1. Voorraadhoeveelheid instellen = 1.
1. Bekijk het product dat u in stap 4 hebt gemaakt met de methode *[!UICONTROL In-Store Delivery]* uit de winkel.
1. Maak een factuur voor de bestelling.
1. Plaats de hoeveelheid van het product aan *0* en maak het uit voorraad.
1. Post de volgende API-aanvraag:

```
{
    "orderIds": [
        1
    ]
}
```

<u> Verwachte resultaten </u>:

E-mailadres klaar om op te halen is niet verzonden.

<u> Ware resultaten </u>:

API keert *orde terug is niet klaar voor bestelwagen*, maar klaar om e-mail op te halen wordt verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ Patches beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
