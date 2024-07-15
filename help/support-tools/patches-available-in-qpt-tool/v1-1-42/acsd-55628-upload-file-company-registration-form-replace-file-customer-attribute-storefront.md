---
title: "ACSD-55628: Bestand uploaden op bedrijfsregistratieformulier; bestand vervangen voor klantkenmerk op winkel"
description: Pas de ACSD-55628-patch toe om het Adobe Commerce-probleem te verhelpen door een bestand op het bedrijfsregistratieformulier te uploaden en een bestand voor een klantkenmerk in de winkel te vervangen.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628: Bestand uploaden op bedrijfsregistratieformulier; bestand vervangen voor klantkenmerk op winkel

>[!NOTE]
>
>Dit flard vervangt [ ACSD-51240 ](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

De ACSD-55628-patch verhelpt het probleem met het uploaden van een bestand op het bedrijfsregistratieformulier en het vervangen van een bestand voor een klantkenmerk op de winkel. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-55628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2 &lt; 2.4.5 en 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan een bestand voor een klantkenmerk in de winkel niet vervangen.

<u> Stappen om </u> te reproduceren:

1. Creeer een nieuw klantenattribuut met de volgende waarden:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *ja*
   * *[!UICONTROL Forms to Use In]*: *alle beschikbare opties*

1. Meld u aan als klant op de winkel en open **[!UICONTROL My Account]** > **[!UICONTROL Account Information]** .
1. Upload een nieuwe afbeelding en sla deze op.
1. Vernieuw de pagina. Verwijder de oude afbeelding en upload een nieuwe. Sla de wijzigingen op.

<u> Verwachte resultaten </u>:

De nieuwe afbeelding wordt opgeslagen.

<u> Ware resultaten </u>:

De oude afbeelding wordt nog steeds weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
