---
title: '''ACSD-53414: gebruikers met beperkte beheerdersrechten kunnen CMS-pagina''s zien die buiten het bereik van hun machtigingen vallen'''
description: Pas de ACSD-53414-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een gebruiker met beperkte beheerdersrechten CMS-pagina's kan zien die buiten het bereik van zijn bevoegdheden vallen.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414: gebruikers met beperkte beheerdersrechten kunnen CMS-pagina&#39;s zien die buiten het bereik van hun machtigingen vallen

De ACSD-53414-patch verhelpt het probleem waarbij een beperkte gebruiker CMS-pagina&#39;s kan zien die buiten het bereik van zijn bevoegdheden vallen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-53414. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte admin-gebruikers kunnen CMS-pagina&#39;s zien die buiten het bereik van hun machtigingen vallen.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website (sub_website), store (sub_store) en storeview (sub_storeview).
1. Creeer een sub_expert rol, die het werkingsgebied van sub_website en sub_store toestaat. Alleen de volgende machtigingen toewijzen: [!UICONTROL Dashboard] en [!UICONTROL Pages].
1. Creeer een nieuwe admin gebruiker en wijs het aan sub_expert rol toe.
1. Wijs de volgende CSM-pagina&#39;s toe aan sub_storeview en standaard storeview.

   * [!UICONTROL 404 Not Found] > Substorevening
   * [!UICONTROL 503 Service Unavailable] > Standaardweergave

1. Meld u aan bij de beheerder met de beheerder die u in Stap 3 hebt gemaakt.
1. Controleer het CMS-paginaraster.

<u>Verwachte resultaten</u>:

*[!UICONTROL 503 Service Unavailable]* is niet zichtbaar voor de webbeheerder.

<u>Werkelijke resultaten</u>:

*[!UICONTROL 503 Service Unavailable]* is zichtbaar voor de webbeheerder.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
