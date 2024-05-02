---
title: '''ACSD-51431: Indexerstatus is *[!UICONTROL Working]* ook al bevat de wijziging geen vermeldingen. "'
description: Pas de ACSD-51431-patch toe om het Adobe Commerce-probleem op te lossen waarbij de indexeerstatus * is[!UICONTROL Working]* ook al bevat de wijziging geen items.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: Indexerstatus is *[!UICONTROL Working]* ook al bevat de wijziging geen items

De ACSD-51431-patch verhelpt het prestatieprobleem waarbij de indexeerstatus *[!UICONTROL Working]* ook al bevat de wijziging geen items. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51431. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De indexeerstatus is *[!UICONTROL Working]* ook al bevat de wijziging geen items.

<u>Stappen om te reproduceren</u>:

1. Set **[!UICONTROL indexers]** tot [!UICONTROL Update on Schedule].
1. Configureer de uitsnijdtaak die elke minuut moet worden uitgevoerd.
1. Sla de wijzigingen in verschillende producten tegelijk op.
1. Uitvoeren `bin/magento indexer:status` over een paar minuten.

<u>Verwachte resultaten</u>:

De wijzigingen worden verwerkt en de indexen bevinden zich in *[!UICONTROL Ready]* status. De *[!UICONTROL Schedule]* status is *[!UICONTROL idle (0 in the backlog)]*.

<u>Werkelijke resultaten</u>:

De wijzigingen worden verwerkt en de indexen bevinden zich in *[!UICONTROL Ready]* status. De *[!UICONTROL Schedule]* statusweergaven *[!UICONTROL working (0 in the backlog)]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
