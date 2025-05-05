---
title: 'MDVA-42326: Klanten krijgen een fout bij het afrekenen na sessietime-out'
description: De MDVA-42326-patch lost het probleem op waarbij de klanten een fout krijgen bij het uitchecken na de sessietime-out, zelfs als de Persistent Shopping Cart is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-42326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Klanten krijgen een fout bij het afrekenen na sessietime-out

De MDVA-42326-patch lost het probleem op waarbij de klanten een fout krijgen bij het uitchecken na de sessietime-out, zelfs als de Persistent Shopping Cart is ingeschakeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 geïnstalleerd is. De patch-id is MDVA-42326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten krijgen een fout bij het uitchecken na de sessietime-out, zelfs als de functie voor het permanent winkelen is ingeschakeld.

<u> Eerste vereisten </u>:

1. Ga naar **Config** > **Algemeen** > **Web** > **de Montages van het Koekje Standaard** > **Levensduur van het Koekje** en reeks aan **120**.
1. Ga naar **Config** > **Klanten** > **Configuratie van de Klant** > **Online Opties van Klanten** en plaats beide waarden aan **2**.
1. Ga naar **Config** > **Klanten** > **Persistent het Schepen Kart** en reeks aan **toelaten**.
1. Ga naar **Configuratie** > **Verkoop** > **de Methoden van de Betaling** en zet alle betalingsmethodes behalve **Controle/Geldorde** (het zou moeten worden toegelaten).

<u> Stappen om </u> te reproduceren:

1. Meld u aan als klant en voeg bepaalde producten toe aan de winkelwagentje.
1. Controleer het winkelwagentje.
1. Wacht twee minuten (ingesteld op voorwaarde); de sessie moet een time-out hebben.
1. Klik **gaan aan controle** en verfrissen niet de pagina.
1. Afhandeling als gast, vul het verzendadres in en kies een verzendmethode.
1. Klik **daarna**.
1. Voor de **Controle &amp; van Betalingen** pagina, klik **de Orde van de Plaats**. Aangezien slechts één betalingsmethode is toegestaan, moet de klant de opdracht kunnen plaatsen zonder de betalingsmethode te selecteren.

<u> Verwachte resultaten </u>:

De klant moet de bestelling kunnen plaatsen.

<u> Ware resultaten </u>:

De klant krijgt de volgende fout: *Ontbroken adresbevestiging: E-mail heeft een verkeerd formaat*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
