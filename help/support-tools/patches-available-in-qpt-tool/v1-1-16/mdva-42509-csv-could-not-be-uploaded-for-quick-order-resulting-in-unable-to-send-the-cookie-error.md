---
title: "MDVA-42509: CSV kan niet worden geüpload voor snelle bestelling, waardoor de fout 'Kan het cookie niet verzenden' optreedt."
description: De MDVA-42509-patch lost het probleem op waarbij een CSV niet kon worden geüpload voor snelle bestelling, wat resulteert in *Kan de cookie*-fout niet verzenden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-42509. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509: CSV kan niet worden geüpload voor snelle bestelling, waardoor de fout &#39;Kan het cookie niet verzenden&#39; optreedt

De MDVA-42509-patch lost het probleem op waarbij een CSV niet kan worden geüpload voor snelle bestelling, wat leidt tot *Kan het cookie niet verzenden* fout. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-42509. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een snelle volgorde maakt met een groot aantal producten die een CSV gebruiken, wordt een cookiefout weergegeven: *Kan het cookie niet verzenden*

<u>Stappen om te reproduceren</u>:

1. Snelle volgorde inschakelen door naar **Winkels** > **Instellingen** > **Configuraties** > **Algemeen** > **B2B-functies**.
1. Maak een klantenaccount en ga naar **Snelle bestelling** op de bovenste koppeling.
1. Probeer een snelle orde tot stand te brengen gebruikend CSV die meer dan 100 SKUs heeft.

<u>Verwachte resultaten</u>:

U kunt een snelle orde met een groot aantal SKUs tot stand brengen.

<u>Werkelijke resultaten</u>:

Er wordt een foutbericht weergegeven met betrekking tot de grootte van cookies.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
