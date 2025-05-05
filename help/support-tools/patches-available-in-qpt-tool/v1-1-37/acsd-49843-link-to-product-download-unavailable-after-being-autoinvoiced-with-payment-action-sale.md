---
title: 'ACSD 49843: Koppeling voor het downloaden van producten is niet beschikbaar nadat deze automatisch is gefactureerd met [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Pas de ACSD-49843-patch toe om het Adobe Commerce-probleem op te lossen waarbij de productdownloadkoppeling niet beschikbaar is nadat het geordende item automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale] .
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: Koppeling voor het downloaden van producten is niet beschikbaar nadat deze automatisch is gefactureerd met [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

De ACSD-49843-patch verhelpt het probleem waarbij de koppeling voor het downloaden van het product niet beschikbaar is nadat het geordende item automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale] . Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.37 wordt geïnstalleerd. De patch-id is ACSD-49843. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De koppeling om het product te downloaden is niet beschikbaar nadat het geordende item automatisch is gefactureerd via een online betalingsmethode wanneer [!UICONTROL Payment Action] is ingesteld op [!UICONTROL Intent Sale] .

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Adobe Commerce Admin en navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]** .

   * In [!UICONTROL Payment Action] drop-down, uitgezochte **[!UICONTROL Intent Sale]**, en reeks *[!UICONTROL Enable Card Payments]* aan *ja*.

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**, en zorg ervoor dat het aan *&quot;Gefactureerd&quot;* wordt geplaatst.
1. Meld u aan als klant in de winkel.

   * Voeg een downloadbaar product en een eenvoudig product toe aan het winkelwagentje.
   * Gebruik [!DNL Braintree Pay] om de volgorde te plaatsen met de kaartoptie.

1. Ga naar **[!UICONTROL My Orders]** en zie dat de factuur automatisch voor de orde wordt gecreeerd en dat zowel de puntstatussen *&quot;Gefactualiseerd&quot;* zijn.
1. Ga naar **[!UICONTROL My Downloadable Products]** en controleer of de downloadkoppeling nog niet beschikbaar is.
1. Ga in Beheer naar die bestelling en maak een verzending voor deze bestelling.
1. Ga in de winkel naar **[!UICONTROL My Downloadable Products]** en controleer of de downloadkoppeling nu beschikbaar is.

<u> Verwachte resultaten </u>:

De verbinding van de download is beschikbaar wanneer de downloadbare productstatus *&quot;Gefactureerd&quot;* is.

<u> Ware resultaten </u>:

De verbinding van de download is niet beschikbaar zelfs wanneer de downloadbare productstatus *&quot;Gefactureerd&quot;* zegt. Deze is alleen beschikbaar nadat een transport voor het fysieke product is gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
