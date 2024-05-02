---
title: 'ACSD-50527: Fout bij het opslaan van een pagina met een leeg dynamisch blok'
description: Pas de ACSD-50527-patch toe om het Adobe Commerce-probleem op te lossen waarbij een fout optreedt bij het opslaan van een pagina met een leeg dynamisch blok.
exl-id: 419201f4-7721-47ee-9692-127145f85496
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-50527: Fout bij het opslaan van een pagina met een leeg dynamisch blok

De ACSD-50527-patch verhelpt het probleem waarbij een fout optreedt bij het opslaan van een pagina met een leeg dynamisch blok. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-50527. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op bij het opslaan van een pagina met een leeg dynamisch blok.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Block]** en maak een nieuw dynamisch blok met lege inhoud.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Create or Edit a new page]**.
1. Voeg twee rijelementen aan de inhoud toe. Voeg vervolgens het nieuwe dynamische blok toe dat hierboven is gemaakt.

<u>Verwachte resultaten</u>:

Er wordt geen fout weergegeven voor een dynamisch blok met lege inhoud in de [!DNL Page Builder].

<u>Werkelijke resultaten</u>:

De [!UICONTROL Dynamic Block] placeholder toont de fout:

>[!ERROR]
>
>Er is een onbekende fout opgetreden. Probeer het opnieuw.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
