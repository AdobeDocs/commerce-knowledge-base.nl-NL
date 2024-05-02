---
title: "ACSD-51636: Bedrijfsbeheerder kan geen nieuwe gebruikers toevoegen vanuit de sectie voor klantenaccounts"
description: Pas de ACSD-51636-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de bedrijfsbeheerder geen nieuwe gebruikers kan toevoegen uit de sectie voor de klantenaccount, ondanks dat hij over alle benodigde rollen en machtigingen beschikt.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: Bedrijfsbeheerder kan geen nieuwe gebruikers toevoegen vanuit de sectie voor klantenaccounts

De ACSD-51636-patch verhelpt het probleem waarbij de bedrijfsbeheerder geen nieuwe gebruikers kan toevoegen vanuit de sectie voor de klantenaccount, ondanks dat hij over alle benodigde rollen en machtigingen beschikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-51636. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrijf admin kan geen nieuwe gebruikers van de sectie van de klantenrekening toevoegen ondanks het hebben van alle noodzakelijke rollen en toestemmingen.

Vereisten:

* B2B-module is geïnstalleerd.
* De functionaliteit van het bedrijf wordt toegelaten.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuw bedrijf.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bewerken **[!UICONTROL Company Admin]** tekst naar *Klant*.
1. Meld u aan als klant.
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** en voeg details voor de gebruiker toe en maak het actief.
1. Sla de nieuwe gebruiker op.

<u>Verwachte resultaten</u>

De beheerder kan een nieuwe gebruiker toevoegen.

<u>Werkelijke resultaten</u>

* De beheerder-gebruiker krijgt een foutbericht: *Er is iets misgegaan*.
* De beheerder-gebruiker kan geen nieuwe klant maken.
* Logboek bevat de volgende fout:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
