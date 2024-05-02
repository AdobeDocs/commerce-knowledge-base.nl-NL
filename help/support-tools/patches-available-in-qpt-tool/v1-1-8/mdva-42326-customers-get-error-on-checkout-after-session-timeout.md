---
title: 'MDVA-42326: Klanten krijgen een fout bij het afrekenen na sessietime-out'
description: De MDVA-42326-patch lost het probleem op waarbij de klanten een fout krijgen bij het uitchecken na de sessietime-out, zelfs als de Persistent Shopping Cart is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-42326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: Klanten krijgen een fout bij het afrekenen na sessietime-out

De MDVA-42326-patch lost het probleem op waarbij de klanten een fout krijgen bij het uitchecken na de sessietime-out, zelfs als de Persistent Shopping Cart is ingeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-42326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten krijgen een fout bij het uitchecken na de sessietime-out, zelfs als de functie voor het permanent winkelen is ingeschakeld.

<u>Vereisten</u>:

1. Ga naar **Config** > **Algemeen** > **Web** > **Standaardcookie-instellingen** > **Cookie Lifetime** en instellen op **120**.
1. Ga naar **Config** > **Klanten** > **Klantconfiguratie** > **Opties voor online klanten** en stel beide waarden in op **2**.
1. Ga naar **Config** > **Klanten** > **Blijvende winkelwagentje** en instellen op **Inschakelen**.
1. Ga naar **Config** > **Verkoop** > **Betalingsmethoden** en alle betalingsmethoden uit te schakelen behalve **Cheque/postwissel** (moet zijn ingeschakeld).

<u>Stappen om te reproduceren</u>:

1. Meld u aan als klant en voeg bepaalde producten toe aan de winkelwagentje.
1. Controleer het winkelwagentje.
1. Wacht twee minuten (ingesteld op voorwaarde); de sessie moet een time-out hebben.
1. Klikken **Ga naar uitchecken** en vernieuw de pagina niet.
1. Afhandeling als gast, vul het verzendadres in en kies een verzendmethode.
1. Klikken **Volgende**.
1. Op de **Reviseren en betalen** pagina, klikt u **Opdracht plaatsen**. Aangezien slechts één betalingsmethode is toegestaan, moet de klant de opdracht kunnen plaatsen zonder de betalingsmethode te selecteren.

<u>Verwachte resultaten</u>:

De klant moet de bestelling kunnen plaatsen.

<u>Werkelijke resultaten</u>:

De klant krijgt de volgende fout: *Verificatie van adres is mislukt: e-mail heeft een onjuiste indeling*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
