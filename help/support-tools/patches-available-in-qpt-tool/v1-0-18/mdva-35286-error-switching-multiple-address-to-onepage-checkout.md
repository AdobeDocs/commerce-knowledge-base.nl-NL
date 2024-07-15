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

De patch MDVA-35286 verhelpt de kwestie waar er een fout is als een klant bundelproducten in de kar heeft en van de controle van het Multiadres aan Onepage checkout overschakelt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 geïnstalleerd is. De patch-id is MDVA-35286. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een fout weergegeven als er een bundelproduct in het winkelwagentje staat en de gebruiker de optie Eén pagina-afhandeling probeert te gebruiken nadat de Afhandeling voor meerdere verzendingen is beëindigd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de klantenaccount en voeg meer dan één bundelproduct toe aan het winkelwagentje.
1. Klik op de koppeling om de winkelwagentje weer te geven en te bewerken.
1. Klik de **Controle uit met Veelvoudige Adressen** verbinding.
1. Selecteer verschillende adressen voor producten die aan de kar worden toegevoegd.
1. Klik **terug aan het Shopping Kart**.
1. In de kar, klik **ga aan Controle** te werk.

<u> Verwachte resultaten </u>:

Je wordt omgeleid naar de pagina Afhandeling.

<u> Ware resultaten </u>:

Het foutenbericht wordt getoond: *Er is een fout die uw verzoek* verwerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
