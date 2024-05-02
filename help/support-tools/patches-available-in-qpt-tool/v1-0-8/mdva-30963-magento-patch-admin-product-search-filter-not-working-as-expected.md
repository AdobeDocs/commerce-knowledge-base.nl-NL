---
title: 'MDVA-30963: zoekfilter voor beheerproducten werkt niet naar behoren'
description: De MDVA-30963-patch lost het probleem op waarbij de Commerce Admin en het productzoekfilter niet werken zoals u had verwacht. De waarden die in een werkingsgebied van de archiefmening worden met voeten getreden worden ook overwogen wanneer het filtreren op **Alle opslagmening** het werkingsgebied van de opslagmening. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: zoekfilter voor beheerproducten werkt niet zoals verwacht

De MDVA-30963-patch lost het probleem op waarbij de Commerce Admin en het productzoekfilter niet werken zoals u had verwacht. Waarden die in een bereik van de archiefweergave worden overschreven, worden ook in overweging genomen bij het filteren op **Alle winkelweergave** weergavebereik opslaan. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Set **Winkels** > **Configuratie** > **Catalogus** > **Catalogus** > **Prijs** > **Bereik catalogusprijs** = *Website*.
1. Maak twee websites met twee verschillende valuta&#39;s (de standaardwebsite is bijvoorbeeld een India Store \[Rupee ₹\] en de tweede is de Amerikaanse winkel \[Dollar $\]).
1. Het volgende instellen **Basisvaluta**, **Standaardweergavemunt**, en **Toegestane valuta&#39;s**:
   * **Standaardconfiguratie** = *Amerikaanse dollar (standaard)*
   * **Hoofdwebsite** = *Indiase roepie*
   * **WebsiteUS** = **Standaardinstellingen gebruiken** = *Amerikaanse dollar*
1. Set **Winkels** > **Valuta** = *1:1*.
1. Creeer een test eenvoudig product dat aan beide Websites met de volgende prijzen wordt toegewezen:
   * **Standaardprijs** = **Websiteprijs VS** = *123 USD*
   * **Hoofdprijs website** = *321 roepie*
1. Maak een gebruiker voor subAdmin die alleen toegang heeft tot de Amerikaanse winkel.
1. Ga naar de Amerikaanse winkel en plaats een product in de winkelwagen (voorbeeld: *123 USD*).
1. Meld u aan bij de beheerder met subbeheerder gemaakt (voorbeeld: *Alleen VS-beheerder*).
1. Ga naar **Rapporten** > **Producten in karretjes**.

<u>Verwachte resultaten</u>:

Wanneer het filtreren binnen **Alle winkelweergave** het werkingsgebied van de archiefmening, producten het filtreren zou de waarde moeten krijgen die in dat bepaalde werkingsgebied wordt geplaatst.

<u>Werkelijke resultaten</u>:

De waarden die in een werkingsgebied van de archiefmening worden met voeten getreden worden ook overwogen wanneer het filtreren op het &quot;Al gebied van de opslagmening&quot;van de opslagmening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
