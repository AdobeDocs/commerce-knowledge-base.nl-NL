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

De MDVA-30963-patch lost het probleem op waarbij de Commerce Admin en het productzoekfilter niet werken zoals u had verwacht. De waarden die in een werkingsgebied van de opslagmening worden met voeten getreden worden ook overwogen wanneer het filtreren op **Al het werkingsgebied van de opslagmening van de opslagmening**. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Plaats **opslag** > **Configuratie** > **Catalogus** > **Catalogus** > **Prijs** > **het Toepassingsgebied van de Prijs van de Catalogus** = *Website*.
1. Maak twee websites met twee verschillende valuta&#39;s (de standaardwebsite is bijvoorbeeld een India Store \[Rupee ₹\] en de tweede is de Amerikaanse winkel \[Dollar $\]).
1. Plaats het volgende **,** StandaardMunt van de Vertoning **, en** Toegestane Valuta&#39;s **:**
   * **Standaard Config** = *Amerikaanse Dollar (Gebrek)*
   * **Belangrijkste Website** = *Indiase Rupee*
   * **WebsiteUS** = **Gebrek van het Gebruik** = *Amerikaanse Dollar*
1. Plaats **opslag** > **Winst van de Valuta** = *1:1*.
1. Creeer een test eenvoudig product dat aan beide Websites met de volgende prijzen wordt toegewezen:
   * **Standaardprijs** = **de prijs van de Website van de VS** = *123 USD*
   * **Belangrijkste prijs van de Website** = *321 Rupee*
1. Maak een gebruiker voor subAdmin die alleen toegang heeft tot de Amerikaanse winkel.
1. Ga naar de opslag van de V.S., en zet een product in de kar (Voorbeeld: *123 USD prijs*).
1. Login aan Admin met subAdmin enkel gecreeerd (Voorbeeld: *slechts admin van de VS*).
1. Ga naar **Rapporten** > **Producten in kar**.

<u> Verwachte resultaten </u>:

Wanneer het filtreren binnen **Al opslagmening** opslagmeningswerkingsgebied, producten het filtreren de waarde zou moeten krijgen die in dat bepaalde werkingsgebied wordt geplaatst.

<u> Ware resultaten </u>:

De waarden die in een werkingsgebied van de archiefmening worden met voeten getreden worden ook overwogen wanneer het filtreren op het &quot;Al gebied van de opslagmening&quot;van de opslagmening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
