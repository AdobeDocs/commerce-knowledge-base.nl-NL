---
title: "ACSD-54040: De [!UICONTROL Created] veld is leeg in de volgorde waarin B2B-modules zijn ingeschakeld."
description: Pas de ACSD-54040-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Created] veld is leeg op de pagina met orderdetails wanneer B2B-modules zijn ingeschakeld.
feature: B2B
role: Admin, Developer
exl-id: 5c420b94-43e1-40ac-9482-8a2d42f173d9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-54040: *[!UICONTROL Created]* veld is leeg in de volgorde waarin de B2B-modules zijn ingeschakeld.

De ACSD-54040-patch verhelpt het probleem waarbij de *[!UICONTROL Created]* veld blijft leeg op de pagina met orderdetails wanneer B2B-modules zijn ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54040. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer B2B-modules zijn ingeschakeld, wordt de *[!UICONTROL Created]* veld blijft leeg op de pagina met orderdetails.

<u>Stappen om te reproduceren</u>:

1. Installeer Adobe Commerce met de B2B-module.
1. Maak een nieuwe klant en plaats een bestelling.
1. Ga naar de orderdetails op de voorzijde en controleer de *[!UICONTROL Created]* veld.

<u>Verwachte resultaten</u>:

De *[!UICONTROL Created]* in het veld wordt de datum weergegeven waarop de bestelling is gemaakt.

<u>Werkelijke resultaten</u>:

De *[!UICONTROL Created]* veld is leeg

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
