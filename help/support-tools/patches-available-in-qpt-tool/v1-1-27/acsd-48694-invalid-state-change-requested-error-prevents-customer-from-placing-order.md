---
title: 'ACSD-48694: Door een ongeldige statuswijziging is een fout met betrekking tot de status niet mogelijk dat de klant de order plaatst.'
description: Pas de ACSD-48694-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de fout *Ongeldige statuswijziging aangevraagd* een klant belet een bestelling te plaatsen.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Ongeldige statuswijziging aangevraagd* fout verhindert klant orde te plaatsen

De ACSD-48694-patch verhelpt het probleem waarbij de fout optreedt *Ongeldige statuswijziging aangevraagd* voorkomt dat een klant een bestelling plaatst. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48694. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *Ongeldige statuswijziging aangevraagd* voorkomt dat een klant een bestelling plaatst.

<u>Stappen om te reproduceren</u>:

1. Een kleine vertraging toevoegen tijdens de `/estimate-shipping-methods` verzoek om een `sleep()` om `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` functie, dus de `/estimate-shipping-methods` Het verzoek wordt voltooid na de `/shipping-information` bij het afrekenen van de verzendstap naar de betalingsstap.
1. Configureer de te gebruiken sessie [!DNL Redis] met de *disable_locking: 1* instellen.
1. Openen **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** en *[!UICONTROL Persistent Shopping Cart]*.
1. Meld u aan als klant en voeg een product toe aan het winkelwagentje.
1. Laat de klantenzitting verlopen. Blijvende cookie en het winkelwagentje blijven bestaan.
1. Ga nu naar Afhandeling, voeg het verzendadres toe en navigeer naar de betalingssectie.
1. Ga terug naar de homepage of een andere pagina en meld u aan bij de klantenaccount.
1. Laat de zitting opnieuw verlopen.
1. Ga nu rechtstreeks naar de betalingspagina en navigeer naar de betalingsstap.
1. Plaats de bestelling.

<u>Verwachte resultaten</u>:

* Er is geen fout.
* De bestelling is geplaatst en een *Bedankt* wordt weergegeven.

<u>Werkelijke resultaten</u>:

De fout *Ongeldige statuswijziging aangevraagd* wordt weergegeven, maar de volgorde wordt geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
