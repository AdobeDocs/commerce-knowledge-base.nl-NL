---
title: 'MDVA-34012 patch: attribute checkbox changes in error'
description: Met de MDVA-34012-patch wordt het probleem opgelost waarbij het selectievakje voor een kenmerk wordt gewijzigd nadat een update in de planning is uitgevoerd.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-34012 patch: attribute checkbox changes in error

Met de MDVA-34012-patch wordt het probleem opgelost waarbij het selectievakje voor een kenmerk wordt gewijzigd nadat een update in de planning is uitgevoerd.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw 2.3.1 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Login aan Admin en navigeer aan **Catalogus > Producten**.
1. Bewerk een eenvoudig product.
1. Wijzig de winkelweergave in een specifieke winkelweergave.
1. Sparen het product met **de standaardwaarde van het Gebruik** checkbox die voor een attribuut wordt geselecteerd (Voorbeeld: **laat het attribuut van het Product** toe).
1. Klik op **Nieuwe Update van het Programma** om sommige veranderingen (Voorbeeld te plannen: **Prijs** of **Speciale Prijs** voor een specifieke opslagmening).
1. Wacht tot de wijzigingen zijn voltooid.
1. Controleer het product. Het selectievakje moet uitgeschakeld zijn en moet een specifieke waarde voor het opslagkenmerk hebben.

<u> Verwachte resultaten </u>:

Het selectievakje voor het kenmerk moet hetzelfde blijven en wordt niet gewijzigd na de update van het programma, zoals u had verwacht.

<u> Ware resultaten </u>:

Het selectievakje voor het kenmerk wordt gewijzigd nadat het programma is bijgewerkt.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
