---
title: 'MDVA-41236: Kan geen nieuwe geplande updates maken of bewerken voor product'
description: De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de "Einddatum" eerder is verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: Kan geen nieuwe geplande updates voor het product maken of bewerken

De MDVA-41236-patch verhelpt het probleem dat gebruikers geen nieuwe geplande updates voor het product kunnen maken of bewerken als de &quot;Einddatum&quot; eerder is verwijderd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41236. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen geen nieuwe schema&#39;s maken of bestaande schema&#39;s voor producten bewerken als de &quot;Einddatum&quot; eerder is verwijderd.

<u> Stappen om </u> te reproduceren:

1. Creeer een product met de Status die aan *wordt geplaatst onbruikbaar maken*.
1. Voeg een geplande update toe om dit product in te schakelen.
   * Voeg toekomstige begin- en einddatums toe.
1. Bewerk de geplande update door de **Datum van het Eind** te verwijderen.
1. Bewerk opnieuw het programma en probeer om een **Datum van het Eind** toe te voegen. Er treedt een fout op.
1. Vernieuw de pagina en ga opnieuw naar **Geplande Update** uitgeven.
1. Klik **verwijderen uit update** > **schrapt de update**.
1. De geplande update wordt nu niet weergegeven boven op de productbewerkingspagina.
1. Maak een nieuwe geplande update die de vorige duur overlapt.

<u> Verwachte resultaten </u>:

* Er is geen fout in stap 4. De beheerder kan de geplande update zonder enige fout bijwerken omdat het schema nog niet actief is.
* De beheerder kan de vorige update verwijderen en een nieuwe update maken.

<u> Ware resultaten </u>:

Gebruikers krijgen het volgende foutbericht:

*fout: De toekomstige Update bestaat reeds in deze tijdwaaier. Stel een ander bereik in en probeer het opnieuw.*


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
