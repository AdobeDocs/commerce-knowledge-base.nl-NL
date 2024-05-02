---
title: "ACSD-48058: productprijsherdex werkt niet als een gebundeld product geen website krijgt toegewezen"
description: Pas de ACSD-48058-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de productprijsherdex niet werkt als het gebundelde product niet aan een website wordt toegewezen.
exl-id: 691371f1-7f10-4be6-80e4-821e7cf664a6
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48058: productprijsherdex werkt niet als een gebundeld product niet aan de website is toegewezen

De ACSD-48058-patch verhelpt het probleem waarbij de productprijsherdex niet werkt als het gebundelde product niet aan een website wordt toegewezen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48058. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijsherdex van het product werkt niet als het gebundelde product niet aan enige website wordt toegewezen.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en maak een nieuw gebundeld product of bewerk een bestaand gebundeld product.
   * Klik op de knop **[!UICONTROL Product in Websites]** en schakel alle selectievakjes (websites) uit
   * Het product opslaan
1. Voer opnieuw index uit.

<u>Verwachte resultaten</u>:

Opnieuw indexeren is uitgevoerd.

<u>Werkelijke resultaten</u>:

De volgende fout wordt gegenereerd bij het uitvoeren van de index van de productprijs:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
