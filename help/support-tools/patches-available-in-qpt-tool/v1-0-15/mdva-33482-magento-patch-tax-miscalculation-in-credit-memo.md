---
title: "MDVA-33482 patch: tax miscalculation in credit memo"
description: Met de MDVA-33482-patch wordt het probleem opgelost dat de belasting in creditnota's onjuist wordt berekend.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33482 patch: tax miscalculation in credit memo

De patch MDVA-33482 lost het probleem op dat de belasting onjuist wordt berekend in creditnota&#39;s wanneer er geen aanpassingsvergoeding of aanpassingsrestitutie wordt toegepast.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.5 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Configureren **Belastingen**.
1. Een bestelling maken met behulp van twee producten op de achtergrond met behulp van een online betalingsmethode (bijvoorbeeld: [!DNL PayPal Payment Pro]). Zorg ervoor dat alle producten worden belast.
1. Maak twee facturen voor de bestelling.
1. Maak een creditmemo op basis van een van de facturen. De oplossing is niet van toepassing als u een aanpassingsvergoeding of aanpassingsrestitutie wilt toepassen.
1. Controleer de totalen van de creditnota.

<u>Verwachte resultaten</u>:

Er is slechts een gedeeltelijk gefactureerd belastingbedrag in de creditnota opgenomen, zoals verwacht.

<u>Werkelijke resultaten</u>:

Het volledige belastingbedrag wordt weergegeven in de creditnota.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
