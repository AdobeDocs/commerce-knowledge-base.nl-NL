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

De ACSD-49389-patch verhelpt het probleem dat een e-mailbericht met de functie &quot;ready-for-pickup&quot; wordt verzonden door de API wanneer de bestelling niet klaar is voor ophalen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49389. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [Startpagina voor QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De API stuurt een e-mailbericht dat u kunt ophalen wanneer de bestelling nog niet klaar is om te worden opgehaald.

<u>Stappen om te reproduceren</u>:

1. Inschakelen *[!UICONTROL In-Store Delivery]* methode.
1. Maak een aandelenbron met de ophaallocatie ingeschakeld.
1. Maak nieuwe voorraad met behulp van de hoofdwebsite met de hierboven gemaakte bron.
1. Maak een product dat dezelfde bron toewijst.
1. Voorraadhoeveelheid instellen = 1.
1. Ontdek het product dat u in stap 4 hebt gemaakt met de opdracht *[!UICONTROL In-Store Delivery]* van de storefront.
1. Maak een factuur voor de bestelling.
1. Aantal producten instellen op *0* en maakt het uit de voorraad.
1. Plaats de volgende API-aanvraag:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Verwachte resultaten</u>:

E-mailadres klaar om op te halen is niet verzonden.

<u>Werkelijke resultaten</u>:

API-geretourneerd *De bestelling is niet klaar voor ophalen*, maar e-mail kan worden opgehaald is verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
