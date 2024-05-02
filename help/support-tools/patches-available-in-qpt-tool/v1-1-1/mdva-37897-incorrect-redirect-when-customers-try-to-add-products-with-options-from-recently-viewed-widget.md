---
title: "MDVA-37897: Onjuiste omleiding bij het toevoegen van producten van Recent Bekeken"
description: Met de MDVA-37897-patch wordt het probleem van onjuiste omleiding opgelost wanneer gebruikers proberen producten toe te voegen met opties van de onlangs bekeken widget. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 is geïnstalleerd. De patch-id is MDVA-37897. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: Onjuiste omleiding bij het toevoegen van producten van Recent Bekeken

Met de MDVA-37897-patch wordt het probleem van onjuiste omleiding opgelost wanneer gebruikers proberen producten toe te voegen met opties van de onlangs bekeken widget. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 is geïnstalleerd. De patch-id is MDVA-37897. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over onze cloudinfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gebruiker een product probeert toe te voegen vanuit de sectie Onlangs bekeken waarvoor opties moeten worden geselecteerd, wordt de gebruiker omgeleid naar de pagina met productdetails in plaats van naar de pagina met productdetails.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product met aanpasbare opties (Type: keuzerondje).
1. Configureer de widget Onlangs bekeken om producten weer te geven.
1. Bezoek producten met aanpasbare opties, zodat deze worden weergegeven in de widget Onlangs bekeken.
1. Klikken **Toevoegen aan winkelwagentje** op een van de producten in de widget Onlangs bekeken.

<u>Verwachte resultaten</u>:

U wordt omgeleid naar de pagina met productdetails om de opties te kiezen.

<u>Werkelijke resultaten</u>:

Je wordt doorgestuurd naar de pagina met productaanbiedingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce op locatie: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op onze cloud-infrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
