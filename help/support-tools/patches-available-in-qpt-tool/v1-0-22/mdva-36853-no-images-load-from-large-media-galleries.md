---
title: 'MDVA-36853: Geen afbeeldingen laden van grote mediagalerieën'
description: De patch MDVA-36853 verhelpt het probleem wanneer er geen afbeeldingen worden geladen omdat de widget voor het maken van een pagina-mediagalerie niet wordt geladen wanneer u een grote mediadirectory hebt.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: Geen afbeeldingen laden van grote mediagalerieën

De patch MDVA-36853 verhelpt het probleem wanneer er geen afbeeldingen worden geladen omdat de widget voor het maken van een pagina-mediagalerie niet wordt geladen wanneer u een grote mediadirectory hebt.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.2 is geïnstalleerd. De patch-id is MDVA-36853. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Set **Oude medialerie inschakelen** = *Ja* in **Beheer > Opslag > Configuratie > Geavanceerd > Systeem > Media-galerie**.
1. Navigeren naar **Inhoud > Blokken** en maakt u een nieuw CMS-blok of bewerkt u een bestaand CMS-blok.
1. Klik op de knop **Bewerken met Pagebuilder** knop.
1. Voeg een media-element toe.
1. Klik op de knop **Selecteren in galerie** knop.

<u>Verwachte resultaten</u>:

De widget voor mediagalerie en de afbeeldingen van de mediagalerie worden beide geladen, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De widget voor de mediagalerie en de afbeeldingen voor de mediagalerie worden niet geladen als u een grote `pub/media/catalog/product/cache/` directory.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
