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

De ACSD-46815-patch verhelpt het probleem waarbij de implementatie van statische inhoud mislukt wanneer de compacte strategie wordt gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 wordt geïnstalleerd. De patch-id is ACSD-46815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De statische plaatsing van de inhoud ontbreekt wanneer het opstellen met een compacte strategie.

<u> Stappen om </u> te reproduceren:

1. Implementeer de statische inhoud met een compacte strategie door de volgende opdracht uit te voeren:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u> Verwachte resultaten </u>:

De statische plaatsing van de inhoud wordt voltooid zonder enige fout.

<u> Ware resultaten </u>:

De statische plaatsing van de inhoud ontbreekt met een compacte strategie. De volgende fout komt tijdens het plaatsingsproces voor: *de inhoud van /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css file kan niet worden gelezen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
