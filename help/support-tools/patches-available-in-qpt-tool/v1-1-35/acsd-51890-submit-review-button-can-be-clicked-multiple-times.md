---
title: '"ACSD-51890: [!UICONTROL Submit review] kan meerdere keren op de knop worden geklikt.'''
description: Pas de ACSD-51890-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Submit Review] er kan meerdere keren op de knop worden geklikt zonder [!DNL Google reCAPTCHA v3] validatie.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** er kan meerdere keren op de knop worden geklikt zonder **[!DNL Google reCAPTCHA v3]** validatie

>[!NOTE]
>
>Deze pleister wordt vervangen door [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

De ACSD-51890-patch verhelpt het probleem waarbij de **[!UICONTROL Submit Review]** er kan meerdere keren op de knop worden geklikt zonder **[!DNL Google reCAPTCHA v3]** validatie. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 is geïnstalleerd. De patch-id is ACSD-51890. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Submit Review]** u kunt meerdere keren op de knop klikken zonder **[!DNL Google reCAPTCHA v3]** validatie.

<u>Stappen om te reproduceren</u>:

1. Inschakelen **[!DNL Google reCAPTCHA v3]** voor het productonderzoek.
1. De productpagina openen en naar de **[!UICONTROL Review]** en zorg ervoor dat de [!DNL reCAPTCHA] is zichtbaar.
1. Vul het revisieformulier in en klik op de knop **[!UICONTROL Submit Review]** zo snel mogelijk meerdere keren te gebruiken.
1. Open de **[!UICONTROL Review]** van de beheerder.

<u>Verwachte resultaten</u>

Er worden geen dubbele revisies gemaakt.

<u>Werkelijke resultaten</u>

Er worden dubbele revisies gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
