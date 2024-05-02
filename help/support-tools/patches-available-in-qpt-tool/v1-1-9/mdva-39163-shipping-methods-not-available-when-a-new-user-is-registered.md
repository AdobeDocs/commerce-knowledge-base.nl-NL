---
title: "MDVA-39163: Verzendmethoden die niet beschikbaar zijn voor nieuwe geregistreerde gebruikers met producten van gastsessies"
description: Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: Verzendmethoden niet beschikbaar voor nieuwe geregistreerde gebruikers met producten van gastsessies

Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verzendmethoden zijn niet beschikbaar wanneer de nieuwe gebruiker is geregistreerd en producten in de winkelwagen zijn afkomstig van de gastsessie.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Beheerder** > **Winkels** > **Configuratie** > **Verkoop** > **Leveringsmethoden**. Alleen de optie **Platte snelheid** de verzendmethode en alle andere mogelijkheden uitschakelen.
1. In de **Platte snelheid** verzendmethode, selecteer de **Specifiek** land-optie beschikbaar in het dialoogvenster **Schip naar landen van toepassing** het plaatsen en selecteren één land van de lijst (bijvoorbeeld, Verenigde Staten).
1. Ga naar **Beheerder** > **Winkels** > **Configuratie** > **Klant** > **Klantconfiguratie** en instellen **E-mailbevestiging vereisen** tot _Ja_.
1. Een nieuwe e-mailsjabloon maken in **Beheerder** > **Marketing** > **E-mailsjablonen** en laden `Footer (magento/luma)` sjabloon en de sjablooninhoud vervangen door een CMS-blok.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Ga naar **Beheerder** > **Inhoud** > **Ontwerp** > **Configuratie** en selecteer het thema dat betrekking heeft op uw frontend website. Stel de &quot;Voettekstsjabloon&quot; in op de nieuwe e-mailsjabloon die u maakt.
1. Ga naar de voorkant en voeg een product aan de kar toe.
1. Maak een klant; u ontvangt een e-mail ter bevestiging van het e-mailadres. Klik op de koppeling Verificatie. U wordt aangemeld bij de website.
1. Ga naar **Mijn account** en voeg een adres toe. Stel het adresland in op het verzendland dat u eerder hebt ingesteld in de beheerconfiguratie.
1. Ga naar Afrekenen.

<u>Verwachte resultaten</u>:

De verzendmethode is beschikbaar omdat de klant een adres heeft dat compatibel is met het verzendende land.

<u>Werkelijke resultaten</u>:

Verzendmethode is niet beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
