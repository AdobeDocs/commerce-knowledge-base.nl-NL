---
title: 'MDVA-43201: Fout bij gebruik van DOB-veld met landinstelling PT'
description: De patch MDVA-43201 lost het probleem op waar een fout voorkomt wanneer het gebruiken van het DOB klantenattribuut in de vorm van de klantenregistratie voor de Portugese scène. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-43201. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: Fout bij gebruik van DOB-veld met landinstelling PT

De patch MDVA-43201 lost het probleem op waar een fout voorkomt wanneer het gebruiken van het DOB klantenattribuut in de vorm van de klantenregistratie voor de Portugese scène. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-43201. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het kenmerk DOB-klant wordt toegevoegd aan het registratieformulier voor de Portugese landinstelling, geeft het formulier de fout *Argument 1 dat aan iterator_to_array() wordt doorgegeven, moet interface-overdraagbaar, null implementeren*.

<u>Vereisten</u>:

B2B-modules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar Beheer > **Winkels** > **Configuratie** > **Algemeen** > **Landinstellingen**, landinstelling instellen op **Portugees** en klik op **Opslaan**.
1. Cache opnieuw indexeren en wissen.
1. Ga naar **Winkels** > **Kenmerk** > **Klant**.
1. DOB-klantkenmerk openen en instellen **Tonen in winkelcentrum** tot **Ja**.
1. Alles selecteren uit **Te gebruiken formulier**.
1. Sla het kenmerk op.
1. Ga naar de pagina Nieuw account maken aan de voorkant.

<u>Verwachte resultaten</u>:

Het registratieformulier voor klanten in de Portugese winkel geeft geen enkele fout bij het toevoegen van het DOB-kenmerk.

<u>Werkelijke resultaten</u>:

Het registratieformulier voor klanten van de Portugese winkel geeft een fout bij het toevoegen van het DOB-kenmerk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
