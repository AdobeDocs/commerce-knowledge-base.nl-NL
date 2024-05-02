---
title: '"Overzicht: [!DNL Quality Patches Tool] (QPT) v1.0.7'''
description: In deze subsectie vindt u een gedetailleerde beschrijving van de problemen die worden opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) Overzicht versie 1.0.7

In deze subsectie vindt u een gedetailleerde beschrijving van de problemen die worden opgelost door de patches die beschikbaar zijn in [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 omvat de volgende flarden:

1. **MDVA-29148**: Het probleem wordt verholpen wanneer een product wordt gemaakt via een API-aanroep, het aangepaste kenmerk van het product van `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (zoals Multiselect) gebruikt de standaardwaarde niet als er geen waarde in de lading is opgegeven.
1. **29389**: Hiermee verhelpt u het probleem met Geavanceerde rapportage waarbij de optie `analytics_collect_data` cronjob zegt : *De haven moet binnen gastheerparameter (als localhost:3306) worden gevormd*.
1. **30594**: Hiermee wordt het probleem verholpen waarbij een bestelling met meerdere adressen niet kon worden opgeslagen tijdens het uitchecken wanneer FPT is geconfigureerd.
1. **30782**: Hiermee wordt het probleem verholpen waarbij Dynamisch blok wordt weergegeven, ongeacht de tekenregel.
1. **30815**: Hiermee kunt u het probleem verhelpen waarbij u wijzigt hoeveel zoekresultaten worden weergegeven op de pagina met zoekresultaten.
1. **30837 MDVA**: Voegt configuratieopties voor de gratis verzendberekening toe zodat de gebruiker het Minimumbedrag van de Volgorde kan configureren voor gratis verzending op basis van het Subtotaal (of Eindtotaal).
1. **30945**: Hiermee wordt het probleem verholpen waarbij een fataal foutbericht wordt weergegeven bij het bijwerken van winkelwagentjes `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **30972**: Hiermee wordt het probleem verholpen waarbij de aangepaste orderstatus is gewijzigd in *Verwerking* na gedeeltelijke verzending met WebApi.
1. **31007**: Hiermee wordt het probleem verholpen waarbij aangepaste adreskenmerken niet correct worden weergegeven op de pagina met orderdetails in het gebied Mijn account en op de achtergrond.
1. **31021 MDVA**: Hiermee wordt het probleem opgelost waarbij prestatieproblemen optreden in `module-catalog-import-export/Model/Import/Product/Option.php`. Als er meer dan ~100k records zijn in `catalog_product_option` een nieuwe CSV met één product duurt minder dan 10 seconden om te valideren.
1. **MDVA-31224**: Verbetert de prestaties van de `catalog_product_price` herindexering van de bundelproducten.
1. **31282**: Hiermee wordt het probleem opgelost waarbij dubbele autorisaties plaatsvinden op [!DNL Paypal PayFlow Pro] in Adobe Commerce. De dubbele toestemming heeft ook tot gevolg dat de [!DNL PayFlow Pro's] fraudefilters en verdubbeling van transactiekosten.
1. **31343**: Hiermee wordt het probleem verholpen met de verwijderde body-klasse `page-layout-category-full-width` wanneer een categorie gepland is.

Gebruik het menu links om naar een specifieke patchpagina te navigeren.
