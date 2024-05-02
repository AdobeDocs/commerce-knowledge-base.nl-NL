---
title: 'ACSD-46404: Admin-gebruiker kan zich niet aanmelden na upgrade naar 2.4.4'
description: De ACSD-46404-patch lost het probleem op waarbij een beheerder zich niet kan aanmelden na een upgrade naar 2.4.4. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 is geïnstalleerd. De patch-id is ACSD-46404. De kwestie is opgelost in Adobe Commerce 2.4.5.
exl-id: 0aebc879-1128-4be2-a6a8-90d5812c7602
feature: Admin Workspace
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-46404: Admin-gebruiker kan zich niet aanmelden na upgrade naar 2.4.4

De ACSD-46404-patch lost het probleem op waarbij een beheerder zich niet kan aanmelden na een upgrade naar 2.4.4. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19 is geïnstalleerd. De patch-id is ACSD-46404. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan zich niet aanmelden na de upgrade naar 2.4.4.

<u>Stappen om te reproduceren</u>:

1. Aanmelden bij het deelvenster Beheer
1. Ga naar winkel > **Instellingen** > **Configuratie** > **Geavanceerd** > **Systeem** > **Beveiliging**.
1. Stel de maximale sessiegrootte in de beheerder in op **0** en sla deze op.

<u>Verwachte resultaten</u>:

De beheerder kan zich aanmelden.

<u>Werkelijke resultaten</u>:

De beheerder wordt afgemeld en kan zich niet aanmelden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
