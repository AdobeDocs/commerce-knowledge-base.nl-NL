---
title: 'MDVA-42855: Het nieuwe klantenadres wordt niet bewaard aan adresboek tijdens controle '
description: De patch MDVA-42855 lost het probleem op waar het nieuwe klantenadres niet aan het adresboek tijdens controle wordt bewaard. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42855. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 37fc51f4-773e-4bef-9fb1-e6629562b94a
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-42855: Het nieuwe klantenadres wordt niet bewaard aan adresboek tijdens controle

De patch MDVA-42855 lost het probleem op waar het nieuwe klantenadres niet aan het adresboek tijdens controle wordt bewaard. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42855. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het nieuwe klantenadres wordt niet opgeslagen aan het adresboek tijdens het afrekenen.

<u>Stappen om te reproduceren</u>:

1. Maak een klantenaccount en werk het standaardadres voor verzending en facturering bij.
1. Voeg een product toe aan de winkelwagentje en navigeer naar de afrekenpagina.
1. Klik bij verzending op **+ Nieuw adres**.
1. Voer uw nieuwe adres in en houd de **Opslaan in adresboek** selectievakje ingeschakeld.
1. Schakel bij Betaling het selectievakje **Mijn facturerings- en verzendadres zijn hetzelfde** selectievakje.
1. Plaats de bestelling.
1. Controleer het adresboek.

<u>Verwachte resultaten</u>:

Het nieuwe verzendadres wordt opgeslagen in het adresboek.

<u>Werkelijke resultaten</u>:

Het nieuwe verzendadres wordt niet opgeslagen in het adresboek.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
