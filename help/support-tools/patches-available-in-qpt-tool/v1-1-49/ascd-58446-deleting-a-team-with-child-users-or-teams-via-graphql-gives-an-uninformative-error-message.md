---
title: 'ACSD-58446: Het verwijderen van een team met onderliggende gebruikers of teams via GraphQL geeft een niet-informatief foutbericht'
description: Pas de ACSD-58446-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het verwijderen van een team met onderliggende gebruikers of teams via GraphQL een niet-informatief foutbericht retourneert dat niet overeenkomt met de gebruikersinterface.
feature: GraphQL
role: Admin, Developer
exl-id: df9eca9d-4d7a-4d4c-b6aa-59ac538b1aa0
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-58446: Het verwijderen van een team met onderliggende gebruikers of teams via GraphQL geeft een niet-informatief foutbericht

De ACSD-58446-patch verhelpt het Adobe Commerce-probleem waarbij als een team met onderliggende gebruikers of teams via GraphQL wordt verwijderd, een foutbericht wordt geretourneerd dat niet informatief is en niet overeenkomt met de gebruikersinterface. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58446. Het probleem wordt volgens de planning opgelost in Adobe Commerce B2B 1.5.1

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een team met onderliggende gebruikers of teams verwijdert via GraphQL, wordt een foutbericht geretourneerd dat niet informatief is en niet overeenkomt met de gebruikersinterface.

## Vereisten:

Adobe Commerce B2B-modules geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Schakel de functie *[!UICONTROL Company]* in.
1. Maak een nieuw bedrijfsaccount.
1. Meld u aan bij **[!UICONTROL Admin]** en activeer de bedrijfsaccount.
1. Controleer de e-mail en stel een wachtwoord in voor het nieuwe bedrijfsaccount.
1. Creeer een nieuw team voor het bedrijf.
1. Login als bedrijfgebruiker op de Storefront en voeg een nieuwe gebruiker voor het gecreeerde team toe.
1. Login aan **[!UICONTROL Admin]**, maak de bedrijfgebruiker onbruikbaar, en reeks *[!UICONTROL Customer Active]* = *Nr*
1. Verwijder het nieuwe team via GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u> Verwachte resultaten </u>:

Er wordt een informatief foutbericht geretourneerd dat consistent is met de gebruikersinterface.

<u> Ware resultaten </u>:

Er wordt een algemeen intern foutbericht voor de server geretourneerd dat niet overeenkomt met de interface.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
