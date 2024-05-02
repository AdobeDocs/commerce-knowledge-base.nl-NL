---
title: 'ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.'
description: Pas het ACSD-51114-patch toe om de Adobe Commerce-uitgave te corrigeren. Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld

>[!NOTE]
>
>Deze patch is vervangen.

De markering ACSD-51114 verhelpt de producten van de kwestie Willekeurige verdwenen uit grote catalogi wanneer het asynchrone indexeren wordt toegelaten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-5114. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` naar de nieuwste versie te kopiëren en de compatibiliteit op de [[!DNL Quality Patches Tool]:Pagina met patches zoeken].Gebruik de patch-id als zoektrefwoord om de patch te zoeken.

## Probleem

Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Maak een set van 10 producten.
1. Alle indexen instellen op **[!UICONTROL Update on Save]** -modus.
1. Maak een categorie en wijs er alle producten aan toe.
1. Alle producten uitschakelen.
1. Open de categorie en controleer of er geen producten zijn.
1. Alle indexen instellen op **[!UICONTROL Update on Schedule]** -modus.
1. Stel de `DEFAULT_BATCH_SIZE` tot 2 inch  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Laat producten in de volgende orde toe: 1st, 9th, 2nd, 5th, 10th, 3rd.
1. Uitsnijden uitvoeren, opdracht.
1. Open de rubriek opnieuw.

<u>Verwachte resultaten</u>:

Alle ingeschakelde producten worden weergegeven.

<u>Werkelijke resultaten</u>:

Alle toegelaten producten worden niet getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
