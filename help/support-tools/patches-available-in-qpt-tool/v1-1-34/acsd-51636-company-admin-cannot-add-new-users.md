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

De ACSD-51636-patch verhelpt het probleem waarbij de bedrijfsbeheerder geen nieuwe gebruikers kan toevoegen vanuit de sectie voor de klantenaccount, ondanks dat hij over alle benodigde rollen en machtigingen beschikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-51636. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrijf admin kan geen nieuwe gebruikers van de sectie van de klantenrekening toevoegen ondanks het hebben van alle noodzakelijke rollen en toestemmingen.

Vereisten:

* B2B-module is geïnstalleerd.
* De functionaliteit van het bedrijf wordt toegelaten.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw bedrijf.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** .
1. Bewerk **[!UICONTROL Company Admin]** type aan *Klant*.
1. Meld u aan als klant.
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** en voeg details voor de gebruiker toe en activeer deze.
1. Sla de nieuwe gebruiker op.

<u> Verwachte resultaten </u>

De beheerder kan een nieuwe gebruiker toevoegen.

<u> Ware resultaten </u>

* De admin gebruiker krijgt een foutenmelding: *het iets ging verkeerd*.
* De beheerder-gebruiker kan geen nieuwe klant maken.
* Logboek bevat de volgende fout:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
