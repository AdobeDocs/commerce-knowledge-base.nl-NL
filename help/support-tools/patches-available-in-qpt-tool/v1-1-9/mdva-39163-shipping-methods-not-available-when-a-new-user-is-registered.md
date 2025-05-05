---
title: 'MDVA-39163: Verzendmethoden niet beschikbaar voor nieuwe geregistreerde gebruikers met producten van gastsessies'
description: Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: Verzendmethoden niet beschikbaar voor nieuwe geregistreerde gebruikers met producten van gastsessies

Met de MDVA-39163-patch wordt het probleem opgelost waarbij de verzendmethoden niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 geïnstalleerd is. De patch-id is MDVA-39163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verzendmethoden zijn niet beschikbaar wanneer de nieuwe gebruiker is geregistreerd en producten in de winkelwagen zijn afkomstig van de gastsessie.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Admin** > **Opslag** > **Configuratie** > **Verkoop** > **Methoden van de Levering**. Laat slechts het **Vlakke Tarief** verschepen methode toe en maak alles anders onbruikbaar.
1. In het **Vaste Tarief** verschepen methode, selecteer de **Specifieke** landoptie beschikbaar in het **Schip aan Toepasselijke Landen** plaatsen en selecteer één land van de lijst (b.v., Verenigde Staten).
1. Ga naar **Admin** > **Opslag** > **Configuratie** > **Klant** > **de Configuratie van de Klant** en de reeks **vereist E-mailbevestiging** aan _ja_.
1. Creeer een nieuw E-mailMalplaatje in **Admin** > **de Marketing** > **E-mailMalplaatjes** en ladings `Footer (magento/luma)` malplaatje en vervang de malplaatjeinhoud met een blok van CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Ga naar **Admin** > **Inhoud** > **Ontwerp** > **Configuratie** en selecteer het thema dat op uw voorste website betrekking heeft. Stel de &quot;Voettekstsjabloon&quot; in op de nieuwe e-mailsjabloon die u maakt.
1. Ga naar de voorkant en voeg een product aan de kar toe.
1. Maak een klant; u ontvangt een e-mail ter bevestiging van het e-mailadres. Klik op de koppeling Verificatie. U wordt aangemeld bij de website.
1. Ga naar **Mijn Rekening** en voeg een adres toe. Stel het adresland in op het verzendland dat u eerder hebt ingesteld in de beheerconfiguratie.
1. Ga naar Afrekenen.

<u> Verwachte resultaten </u>:

De verzendmethode is beschikbaar omdat de klant een adres heeft dat compatibel is met het verzendende land.

<u> Ware resultaten </u>:

Verzendmethode is niet beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
