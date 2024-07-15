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

De patch MDVA-29148 lost het probleem op waarbij `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` de standaardwaarde voor opslaan niet toewijst. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce on cloud Infrastructure 2.3.3-p1.

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een product wordt gemaakt via een importscript of de REST API, wordt aan kenmerken die het `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` backend-model gebruiken en een standaardwaarde hebben, de standaardwaarde niet toegewezen.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw globaal kenmerk dat het `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` backend-model en een niet-lege standaardwaarde gebruikt.
1. Gebruik de REST API om een nieuw product te maken.
1. Vestig dat nieuwe product van REST API en bevestig dat het attribuut niet aanwezig in de douanekenmerken van het product is.

<u> Verwachte resultaten </u>:

De standaardwaarde van het aangepaste kenmerk is opgeslagen in het kenmerk product.

<u> Ware resultaten </u>:

De standaardwaarde van het aangepaste kenmerk is niet opgeslagen in het productkenmerk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
