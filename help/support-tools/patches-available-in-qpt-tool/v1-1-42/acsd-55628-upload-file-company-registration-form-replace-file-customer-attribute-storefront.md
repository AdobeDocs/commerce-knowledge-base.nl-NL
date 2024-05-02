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
>Deze patch vervangt [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

De ACSD-55628-patch verhelpt het probleem met het uploaden van een bestand op het bedrijfsregistratieformulier en het vervangen van een bestand voor een klantkenmerk op de winkel. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-55628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2 &lt; 2.4.5 en 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan een bestand voor een klantkenmerk in de winkel niet vervangen.

<u>Stappen om te reproduceren</u>:

1. Creeer een nieuw klantenattribuut met de volgende waarden:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Ja*
   * *[!UICONTROL Forms to Use In]*: *alle beschikbare opties*

1. Meld u aan als klant in de winkel en open **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Upload een nieuwe afbeelding en sla deze op.
1. Vernieuw de pagina. Verwijder de oude afbeelding en upload een nieuwe. Sla de wijzigingen op.

<u>Verwachte resultaten</u>:

De nieuwe afbeelding wordt opgeslagen.

<u>Werkelijke resultaten</u>:

De oude afbeelding wordt nog steeds weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
