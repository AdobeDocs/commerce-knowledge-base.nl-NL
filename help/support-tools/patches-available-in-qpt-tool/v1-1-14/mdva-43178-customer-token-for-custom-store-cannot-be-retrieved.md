---
title: 'MDVA-43178: Klanttoken voor aangepast archief kan niet worden opgehaald in GraphQL'
description: De patch MDVA-43178 verhelpt het probleem waarbij de token voor de klant van een aangepaste store niet kan worden opgehaald in GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43178. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b2a8bf96-7534-41d2-b83b-58d8e0b6d076
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-43178: Klanttoken voor aangepast archief kan niet worden opgehaald in GraphQL

De patch MDVA-43178 verhelpt het probleem waarbij de token voor de klant van een aangepaste store niet kan worden opgehaald in GraphQL. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43178. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanttoken voor een aangepaste winkel kan niet worden opgehaald in GraphQL.

<u>Stappen om te reproduceren</u>:

1. Maak twee winkelweergaven voor de standaardwinkel.
1. Maak een nieuwe website, één winkel en één winkelweergave. Geef deze winkelweergave de naam &#39;test3&#39;.
1. Maak een klant voor de nieuwe website.
1. API-beheertoken genereren:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. Verzend GraphQL om klantentoken als beheerder op te halen, gebruik de beheertoken voor verificatie, met &quot;store&quot; = &quot;test3&quot; in de header:

   <pre>
    <customer_email>
      </pre>

<u>Verwachte resultaten</u>:

Klanttoken wordt gegenereerd.

<u>Werkelijke resultaten</u>:

Klanttoken wordt niet gegenereerd. Merchants get *E-mailadres van klant is niet beschikbaar* als reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
