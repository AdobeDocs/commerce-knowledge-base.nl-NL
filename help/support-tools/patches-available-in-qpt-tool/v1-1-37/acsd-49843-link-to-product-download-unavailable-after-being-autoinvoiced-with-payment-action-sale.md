---
title: 'ACSD 49843: Koppeling voor het downloaden van producten is niet beschikbaar nadat deze automatisch is gefactureerd met [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Pas de ACSD-49843-patch toe om het Adobe Commerce-probleem op te lossen waarbij de koppeling voor het downloaden van producten niet beschikbaar is nadat het bestelde item automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: Koppeling voor het downloaden van producten is niet beschikbaar nadat deze automatisch is gefactureerd met [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

De ACSD-49843-patch verhelpt het probleem waarbij de koppeling voor het downloaden van het product niet beschikbaar is nadat het bestelde item automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale]. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.37 is geïnstalleerd. De patch-id is ACSD-49843. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De koppeling om het product te downloaden is niet beschikbaar nadat het bestelde object automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale].

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Adobe Commerce Admin en navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * In de [!UICONTROL Payment Action] vervolgkeuzelijst, selecteert u **[!UICONTROL Intent Sale]**, en instellen *[!UICONTROL Enable Card Payments]* tot *Ja*.

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** en zorgt ervoor dat deze is ingesteld op *&quot;Factuurd&quot;*.
1. Meld u aan als klant in de winkel.

   * Voeg een downloadbaar product en een eenvoudig product toe aan het winkelwagentje.
   * Gebruiken [!DNL Braintree Pay] om de bestelling te plaatsen met de optie Kaart.

1. Ga naar **[!UICONTROL My Orders]** en ziet u dat de factuur automatisch wordt aangemaakt voor de bestelling en dat beide statussen *&quot;Factuurd&quot;*.
1. Ga naar **[!UICONTROL My Downloadable Products]** en controleer of de downloadkoppeling nog niet beschikbaar is.
1. Ga in Beheer naar die bestelling en maak een verzending voor deze bestelling.
1. Ga in de winkel naar **[!UICONTROL My Downloadable Products]** en controleer of de downloadkoppeling nu beschikbaar is.

<u>Verwachte resultaten</u>:

De downloadkoppeling is beschikbaar wanneer de downloadbare productstatus is *&quot;Factuurd&quot;*.

<u>Werkelijke resultaten</u>:

De downloadkoppeling is zelfs niet beschikbaar als de status van het downloadbare product aangeeft *&quot;Factuurd&quot;*. Deze is alleen beschikbaar nadat een transport voor het fysieke product is gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
