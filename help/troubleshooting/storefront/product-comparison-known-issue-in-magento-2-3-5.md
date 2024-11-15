---
title: Bekende kwestie in Adobe Commerce 2.3.5 voor de vergelijking van producten
description: Dit artikel bevat aanbevelingen voor het voorkomen van een bekend probleem met [productvergelijking] (https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) in Adobe Commerce op locatie 2.3.5 en Adobe Commerce op cloudinfrastructuur 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Bekende kwestie in Adobe Commerce 2.3.5 voor de vergelijking van producten

Dit artikel verstrekt aanbevelingen op hoe te om een bekende ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) kwestie van de 0} productvergelijking {in Adobe Commerce op-gebouw 2.3.5 en Adobe Commerce op wolkeninfrastructuur 2.3.5 te vermijden.[

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.5
* Adobe Commerce over wolkeninfrastructuur 2.3.5

## Probleem

Wanneer een gebruiker probeert om producten van verschillende opslagmeningen te vergelijken en één product een lege waarde voor een vergelijkbaar attribuut heeft, toont Adobe Commerce een bedorven Compare pagina van Producten.

## Oplossing

Geef niet-lege waarden op voor vergelijkbare productkenmerken of gebruik de standaardwaarde voor de winkelweergave voor het kenmerk. Vergelijkbare kenmerkwaarden mogen niet leeg zijn.

>[!NOTE]
>
>De attributen van het product worden geplaatst om voor vergelijking worden gebruikt gebruikend **Vergelijkbaar op configuratie het plaatsen van de Configuratie Storefront**. Voor meer informatie, verwijs naar [ Creërend de Attributen van het Product ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties) in onze gebruikersgids.

Een oplossing is beschikbaar in Adobe Commerce 2.3.6, dat volgens de planning in het vierde kwartaal van 2020 zal worden uitgebracht.

U kunt de moeilijke situatie in GitHub bekijken (gelieve te bedenken, dat de moeilijke situatie niet door regressietests ging en geen officiële hete moeilijke situatie is): <https://github.com/magento/magento2/pull/27662>

## Gerelateerde lezing

<ul><li>Adobe Commerce Support Knowledge Base-artikelen voor bekende problemen met Adobe Commerce 2.3.5:<ul>
<li>
<p title="Opdrachten voor meerdere verzendingen met een virtueel product worden niet correct verwerkt in Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Opdrachten voor meerdere verzendingen met een virtueel product worden niet correct verwerkt in Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Bulkactie product count known issue in Adobe Commerce 2.3.5</a></li>
<li>
<p title="Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues"> Adobe Commerce 2.3.5 Bekende Kwesties </a> in onze ontwikkelingsdocumentatie</li></ul>
