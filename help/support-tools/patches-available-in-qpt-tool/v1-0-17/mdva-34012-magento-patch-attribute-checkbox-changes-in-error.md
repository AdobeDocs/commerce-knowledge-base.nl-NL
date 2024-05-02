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

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.1 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij Beheer en navigeer naar **Catalogus > Producten**.
1. Bewerk een eenvoudig product.
1. Wijzig de winkelweergave in een specifieke winkelweergave.
1. Sla het product op met de **Standaardwaarde gebruiken** Selectievakje geselecteerd voor een kenmerk (voorbeeld: **Product inschakelen** kenmerk).
1. Klikken op **Nieuwe update plannen** om enkele wijzigingen te plannen (Voorbeeld: **Prijs** of **Speciale prijs** voor een specifieke winkelweergave).
1. Wacht tot de wijzigingen zijn voltooid.
1. Controleer het product. Het selectievakje moet uitgeschakeld zijn en moet een specifieke waarde voor het opslagkenmerk hebben.

<u>Verwachte resultaten</u>:

Het selectievakje voor het kenmerk moet hetzelfde blijven en wordt niet gewijzigd na de update van het programma, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Het selectievakje voor het kenmerk wordt gewijzigd nadat het programma is bijgewerkt.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
