---
title: "ACSD-46767: [!UICONTROL Category] pagina caches ongeldig maken wanneer het voorraadaantal verandert"
description: Pas de ACSD-46767-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Category] paginacaches ongeldig maken wanneer de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] paginakaarten ongeldig maken wanneer het voorraadaantal verandert

De ACSD-46767-patch verhelpt het probleem waarbij de [!UICONTROL Category] paginacaches ongeldig maken wanneer de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 is geïnstalleerd. De patch-id is ACSD-46767. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Category] paginakaarten ongeldig maken wanneer het voorraadaantal verandert.

<u>Stappen om te reproduceren</u>:

1. Maak enkele producten en voeg deze toe aan dezelfde categorie.
1. Open de *[!UICONTROL Category]* pagina in de opslagruimte om ervoor te zorgen dat de pagina in de cache wordt opgeslagen.
1. Plaats de bestelling bij een van de producten uit de categorie *(producthoeveelheid is gewijzigd, maar product is nog in voorraad)*.
1. Open de [!UICONTROL Category] weer in de winkelruimte.

<u>Werkelijke resultaten</u>:

De pagina wordt niet vanuit de cache geladen. Het wordt opnieuw gegenereerd.

<u>Verwachte resultaten</u>:

De pagina wordt uit de cache geladen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
