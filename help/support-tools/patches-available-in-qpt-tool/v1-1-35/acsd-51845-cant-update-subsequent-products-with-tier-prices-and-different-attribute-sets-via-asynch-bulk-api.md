---
title: "ACSD-51845: Kan volgende producten met prijzen op lagen en verschillende kenmerksets niet bijwerken via asynchrone bulksgewijs [!DNL API]"
description: Pas de ACSD-51845-patch toe om het Adobe Commerce-probleem op te lossen, waarbij u volgende producten niet via asynchrone bulksgewijs kunt bijwerken met prijzen op lagen en verschillende kenmerksets [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: Kan volgende producten met prijzen op lagen en verschillende kenmerksets niet bijwerken via asynchrone bulksgewijs [!DNL API]

De ACSD-51845-patch verhelpt het probleem dat u volgende producten met prijzen op lagen en verschillende kenmerksets niet via asynchrone bulksgewijs kunt bijwerken [!DNL REST API]. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-51845. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Update mislukt voor volgende producten met laagprijzen en verschillende kenmerksets via asynchrone bulksgewijs [!DNL REST API].

<u>Stappen om te reproduceren</u>:

1. Configureren [!DNL RabbitMQ].
1. Maak twee kenmerkensets.
1. Twee maken **Eenvoudige producten**, waarbij elk product wordt toegewezen aan een andere kenmerkset.
1. Voeg een **Prijs van klantengroep** voor elk product.
1. Beide producten in dezelfde bulk bijwerken [!DNL API] bijwerken.
1. Zorg ervoor dat de `bin/magento queue:consumers:start async.operations.all` wordt uitgevoerd.
1. De massa controleren [!DNL API] status.

<u>Verwachte resultaten</u>:

De service is uitgevoerd.

<u>Werkelijke resultaten</u>:

Het systeem retourneert het foutbericht: *Kan het product niet opslaan. Probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
