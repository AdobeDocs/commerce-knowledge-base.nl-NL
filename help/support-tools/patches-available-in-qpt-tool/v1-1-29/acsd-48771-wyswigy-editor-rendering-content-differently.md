---
title: 'ACSD-48771: inhoud wordt in de WYSIWYG-editor anders gerenderd'
description: Pas de ACSD-48771-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de WYSIWYG-editor inhoud anders weergeeft.
exl-id: 6a856fa3-6099-4237-8d1c-e3735b8ca012
feature: Cache, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-48771: inhoud wordt in de WYSIWYG-editor anders weergegeven

De ACSD-48771-patch verhelpt het probleem waarbij de WYSIWYG-editor inhoud anders weergeeft. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-48771. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De WYSIWYG-editor geeft de inhoud anders weer.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin, creeer een nieuwe pagina met een rij met drie kolommen, en sla de pagina op.
1. Werk Adobe Commerce bij naar een van de meest recente versies.
1. Set [!DNL Chrome] browser om cache en snelheid uit te schakelen naar *Snel 3G*.
1. Ga nogmaals naar de bewerkingspagina en vernieuw deze totdat de kolommen rijen worden.
1. Sla de pagina op terwijl de kolommen in rijen staan.

<u>Verwachte resultaten</u>:

De constructor van de Admin-pagina mag geen kolommen in rijen weergeven.

<u>Werkelijke resultaten</u>:

Kolommen worden in verschillende rijen weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
