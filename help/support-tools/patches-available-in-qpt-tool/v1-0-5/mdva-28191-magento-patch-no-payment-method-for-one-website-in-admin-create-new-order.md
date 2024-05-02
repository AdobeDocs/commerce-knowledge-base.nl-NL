---
title: 'MDVA-28191: Geen betalingsmethode voor één website in Admin Create New Order'
description: De MDVA-28191-patch verhelpt het probleem dat een betalingsmethode niet wordt geladen in Beheer **Nieuwe bestelling maken** voor één website, hoewel betalingsmethoden mogelijk worden weergegeven voor andere websites.  Deze patch is beschikbaar wanneer het gereedschap [QPT (Quality Patches Tool)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.5 is geïnstalleerd.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: Geen betalingsmethode voor één website in Admin Create New Order

De MDVA-28191-patch verhelpt het probleem waarbij een betalingsmethode niet wordt geladen in de Admin **Nieuwe volgorde maken** voor één website, hoewel betalingsmethoden voor andere websites kunnen worden weergegeven.  Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) is geïnstalleerd.

## Betrokken producten en versies

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3 tot 2.4.1 (inclusief 2.3.5-p1).

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u een volgorde maakt op basis van de backend-Adobe Commerce, worden twee aanhalingstekens gemaakt, de ene is inactief en de andere is actief. Maar de zitting houdt inactieve citaat identiteitskaart

<u>Stappen om te reproduceren</u>

1. Ga naar **Deelvenster Beheer** > **Verkoop** > **Orders** en klik op de knop **Nieuwe volgorde maken** knop.
1. Kies de klant voor wie u de bestelling wilt maken.
1. Als uw winkel meerdere weergaven heeft, kiest u de winkelweergave waar de bestelling moet worden geplaatst in het dialoogvenster **Nieuwe volgorde maken** pagina voor de gebruiker die u hebt geselecteerd.
1. Producten toevoegen uit de **Activiteiten van de klant** in of uit de catalogus door op **Producten toevoegen**. Schuif omlaag op de pagina om de volgende secties naar wens in te vullen voor de volgorde:
   * Couponcodes toepassen
   * Betalingsmethode
   * Verzendmethode
   * Opmerkingen bestellen

<u>Verwacht resultaat:</u>

Betalingsmethoden moeten voor alle websites worden geladen in de beheerder.

<u>Werkelijk resultaat:</u>

Geen betalingsmethode beschikbaar (geen van beide berichten &quot;*Geen betalingsgegevens vereist*&quot; weergegeven) voor deze website, hoewel betalingsmethoden kunnen worden weergegeven bij het testen van bestellingen voor andere websites.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
