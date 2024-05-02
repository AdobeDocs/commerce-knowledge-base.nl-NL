---
title: 'ACSD-46815: implementatie van statische inhoud mislukt bij gebruik van compacte strategie'
description: Pas de ACSD-46815-patch toe om het Adobe Commerce-probleem op te lossen waarbij de implementatie van statische inhoud mislukt bij gebruik van een compacte strategie.
exl-id: e94a0911-5cd9-4866-a027-7ea3239555d3
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-46815: implementatie van statische inhoud mislukt bij gebruik van compacte strategie

De ACSD-46815-patch verhelpt het probleem waarbij de implementatie van statische inhoud mislukt wanneer de compacte strategie wordt gebruikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 is geïnstalleerd. De patch-id is ACSD-46815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De statische plaatsing van de inhoud ontbreekt wanneer het opstellen met een compacte strategie.

<u>Stappen om te reproduceren</u>:

1. Implementeer de statische inhoud met een compacte strategie door de volgende opdracht uit te voeren:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Verwachte resultaten</u>:

De statische plaatsing van de inhoud wordt voltooid zonder enige fout.

<u>Werkelijke resultaten</u>:

De statische plaatsing van de inhoud ontbreekt met een compacte strategie. De volgende fout komt tijdens het plaatsingsproces voor: *De inhoud van /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css file kan niet worden gelezen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
