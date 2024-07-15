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

Het flard MDVA-28191 bevestigt de kwestie waar een betalingsmethode niet in Admin **leidt tot Nieuwe Orde** voor één website, hoewel de betalingsmethodes voor andere websites kunnen tonen.  Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) hulpmiddelversie 1.0.5 geïnstalleerd is.

## Betrokken producten en versies

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3 tot 2.4.1 (inclusief 2.3.5-p1).

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u een volgorde maakt op basis van de backend-Adobe Commerce, worden twee aanhalingstekens gemaakt, de ene is inactief en de andere is actief. Maar de zitting houdt inactieve citaat identiteitskaart

<u> Stappen om te reproduceren </u>

1. Ga naar **Comité Admin** > **Verkoop** > **Orden** en klik **creeer Nieuwe Orde** knoop.
1. Kies de klant voor wie u de bestelling wilt maken.
1. Als uw opslag veelvoudige meningen heeft, kies de opslagmening waar de orde moet worden geplaatst, op **creeer Nieuwe Opdracht** pagina voor de gebruiker u selecteerde.
1. Voeg producten van de **sectie van de Activiteiten van de Klant 0} toe {of van de catalogus door** te klikken voeg Producten **toe.** Schuif omlaag op de pagina om de volgende secties naar wens in te vullen voor de volgorde:
   * Couponcodes toepassen
   * Betalingsmethode
   * Verzendmethode
   * Opmerkingen bestellen

<u> Verwacht resultaat:</u>

Betalingsmethoden moeten voor alle websites worden geladen in de beheerder.

<u> Ware resultaat:</u>

Geen betalingsmethode beschikbaar (noch is het bericht &quot;*Geen Vereiste Informatie van de Betaling*&quot;getoond) voor deze website, hoewel de betalingsmethodes kunnen tonen wanneer het testen van orden voor andere websites.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
