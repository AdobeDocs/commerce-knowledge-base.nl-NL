---
title: 'ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan'
description: Pas de ACSD-48164-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: beperkte beheerder kan waarde op websiteniveau niet opslaan

De ACSD-48164-patch verhelpt het probleem waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen geen waarde op websiteniveau opslaan.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website, sla deze op en sla de weergave op in [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Een nieuwe beheerdersrol maken in [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Ga naar **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, selecteert u de nieuwe website en wijst u deze rol toe aan elke gebruiker van de beheerder.

1. Selecteer een willekeurig product en wijs alleen de nieuwe website toe. Selecteer de standaardwebsite niet.
1. Meld u aan als de beheerder die in stap 2 is toegewezen en bewerk het product onder **[!UICONTROL All Store View]** bereik wijzigen door kenmerk op websiteniveau te wijzigen, zoals *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* en stelt u het product in als nieuw.
1. Sla het product op.

<u>Verwachte resultaten</u>:

De gebruiker van Admin verbonden aan het rolwerkingsgebied aan één website kan productattributen op website-niveau bewaren gebruikend *[!UICONTROL All Store View]* bereik.

<u>Werkelijke resultaten</u>:

Het succesbericht dat het product is opgeslagen, verschijnt, maar de waarden van de productkenmerken blijven ongewijzigd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
