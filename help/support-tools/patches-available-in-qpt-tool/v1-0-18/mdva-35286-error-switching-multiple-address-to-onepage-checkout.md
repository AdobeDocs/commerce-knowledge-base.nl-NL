---
title: 'MDVA-35286: fout die Veelvoudig Adres overschakelt aan Onepage checkout'
description: De patch MDVA-35286 verhelpt de kwestie waar er een fout is als een klant bundelproducten in de kar heeft en van de controle van het Multiadres aan Onepage checkout overschakelt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-35286. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: fout die Veelvoudig Adres overschakelt aan Onepage checkout

De patch MDVA-35286 verhelpt de kwestie waar er een fout is als een klant bundelproducten in de kar heeft en van de controle van het Multiadres aan Onepage checkout overschakelt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-35286. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een fout weergegeven als er een bundelproduct in het winkelwagentje staat en de gebruiker de optie Eén pagina-afhandeling probeert te gebruiken nadat de Afhandeling voor meerdere verzendingen is beëindigd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de klantenaccount en voeg meer dan één bundelproduct toe aan het winkelwagentje.
1. Klik op de koppeling om de winkelwagentje weer te geven en te bewerken.
1. Klik op de knop **Uitchecken met meerdere adressen** koppeling.
1. Selecteer verschillende adressen voor producten die aan de kar worden toegevoegd.
1. Klikken **Terug naar Winkelwagentje**.
1. Klik in de winkelwagen op **Doorgaan naar Afhandeling**.

<u>Verwachte resultaten</u>:

Je wordt omgeleid naar de pagina Afhandeling.

<u>Werkelijke resultaten</u>:

Het foutbericht wordt weergegeven: *Er is een fout opgetreden bij het verwerken van uw verzoek*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
