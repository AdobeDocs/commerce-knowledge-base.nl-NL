---
title: 'Overzicht: [!DNL Quality Patches Tool]  (QPT) v1.0.7'
description: Deze subsectie verstrekt een gedetailleerde beschrijving van de kwesties die door de flarden beschikbaar in  [!DNL Quality Patches Tool]  (QPT) v1.0.7 worden opgelost.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Overzicht van [!DNL Quality Patches Tool] (QPT) v1.0.7

Deze subsectie bevat een gedetailleerde beschrijving van de problemen die zijn opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 omvat de volgende flarden:

1. **MDVA-29148**: Verhelpt de kwestie wanneer het creëren van een product via een API vraag, gebruikt het attribuut van de productdouane van `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (als Multiselect) type niet zijn standaardwaarde als geen waarde in de nuttige lading werd verstrekt.
1. **MDVA-29389**: Verhelpt de kwestie met Geavanceerde Rapportering waar `analytics_collect_data` kronjob zegt: *de Haven moet binnen gastheerparameter (als localhost worden gevormd:3306)*.
1. **MDVA-30594**: Verhelpt de kwestie waar een orde met veelvoudige adressen niet tijdens controle kon worden bewaard wanneer FPT wordt gevormd.
1. **MDVA-30782**: Verhelpt de kwestie waar het Dynamische Blok ongeacht de wortelregel wordt getoond.
1. **MDVA-30815**: Verhelpt de kwestie waar wanneer u verandert hoeveel onderzoeksresultaten op de pagina van onderzoeksresultaten zouden moeten worden getoond.
1. **mDVA-30837**: Voegt configuratieopties voor de vrije verschepende berekening toe zodat kan de gebruiker het Minimale Bedrag van de Orde vormen om Vrije Verzending te krijgen die op Subtotal (of het Grote Totaal) wordt gebaseerd.
1. **MDVA-30945**: Verhelpt de kwestie waar u een fatale foutenmelding wanneer het bijwerken van kaarten `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` ontvangt.
1. **MDVA-30972**: Verhelpt de kwestie waar de status van de douaneorde in *Verwerking* na gedeeltelijke ladingsverwezenlijking gebruikend WebApi werd veranderd.
1. **MDVA-31007**: Bevestigt de kwestie waar de attributen van het douaneadres niet correct in de pagina van de ordedetails in het mijn rekeningsgebied en in het achtereind worden getoond.
1. **MDVA-31021**: Verhelpt de kwestie waar de prestatieskwesties in `module-catalog-import-export/Model/Import/Product/Option.php` bestaan. Als er meer dan ~100k verslagen in `catalog_product_option` lijst zijn, duurt een nieuw CSV met enig product minder dan 10 sec om te bevestigen.
1. **MDVA-31224**: verbetert de prestaties van `catalog_product_price` re-indexverrichting voor bundelproducten.
1. **MDVA-31282**: Verhelpt de kwestie waar de dubbele vergunningen op [!DNL Paypal PayFlow Pro] in Adobe Commerce voorkomen. De dubbele autorisaties hebben ook tot gevolg dat [!DNL PayFlow Pro's] -frauduleuze filters worden overgeslagen en transactiekosten worden verdubbeld.
1. **MDVA-31343**: Verhelpt de kwestie met de verwijderde lichaamscategorie `page-layout-category-full-width` wanneer een categorie gepland is.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.
