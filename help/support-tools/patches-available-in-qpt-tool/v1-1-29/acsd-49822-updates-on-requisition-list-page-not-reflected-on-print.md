---
title: 'ACSD-49822: Updates op pagina met aanvraaglijsten die niet worden weergegeven in de lijst met afdrukverzoeken'
description: Pas de ACSD-49822-patch toe om het Adobe Commerce-probleem op te lossen, waarbij updates op de pagina met de aanvraaglijst niet worden weergegeven in de lijst met afdrukverzoeken.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: Updates in de aanvraaglijst worden niet weergegeven in de lijst met afdrukaanvragen

De ACSD-49822-patch verhelpt het probleem dat updates op de pagina met de aanvraaglijst niet worden weergegeven in de lijst met afdrukverzoeken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49822. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Updates op de pagina met aanvraaglijsten worden niet weergegeven in de lijst met afdrukverzoeken.

<u> Stappen om </u> te reproduceren:

1. Laat verzoeklijst toe door aan **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** te navigeren > **[eigenschappen B2B]**.
1. Maak een product.
1. Meld u aan als klant en voeg twee producten toe aan de aanvraaglijst.
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]** .
1. Een aanvraaglijst weergeven.
1. Klik op **[!UICONTROL Print]** in de rechterbovenhoek.
1. Sluit het afdrukvenster en de pagina met de lijst met afdrukaanvragen.
1. Verwijder een item in de lijst of werk een aantal items bij en probeer het opnieuw af te drukken.
1. U ziet dat de items niet worden bijgewerkt in het afdrukvenster.
1. Sluit het afdrukvenster.
1. U ziet dat de items niet worden bijgewerkt op de afdrukpagina van de aanvraaglijst.

<u> Verwachte resultaten </u>:

De lijst die moet worden afgedrukt, wordt bijgewerkt nadat eventuele wijzigingen zijn aangebracht.

<u> Ware resultaten </u>:

Updates worden niet weergegeven op de afdrukpagina van de aanvraaglijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
