---
title: 'MDVA-29148: ArrayBackend wijst geen standaardwaarde toe bij opslaan'
description: De patch MDVA-29148 lost het probleem op waarbij ` \Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend ` niet de standaardwaarde op sparen toewijst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend wijst geen standaardwaarde toe bij sparen

De MDVA-29148-patch lost het probleem op waarbij `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` Hiermee wordt bij het opslaan de standaardwaarde niet toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce on cloud Infrastructure 2.3.3-p1.

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een product wordt gemaakt via een importscript of de REST API, worden kenmerken gebruikt die `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` aan het back-endmodel en een standaardwaarde hebben, wordt de standaardwaarde niet toegewezen.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuw globaal kenmerk dat het `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` achtergrondmodel en een niet-lege standaardwaarde.
1. Gebruik de REST API om een nieuw product te maken.
1. Vestig dat nieuwe product van REST API en bevestig dat het attribuut niet aanwezig in de douanekenmerken van het product is.

<u>Verwachte resultaten</u>:

De standaardwaarde van het aangepaste kenmerk is opgeslagen in het kenmerk product.

<u>Werkelijke resultaten</u>:

De standaardwaarde van het aangepaste kenmerk is niet opgeslagen in het productkenmerk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
