---
title: '[!UICONTROL salesRule] labels geven bij upgrade van versies &lt; 2,4,5'
description: Pas een patch toe om de **[!UICONTROL salesRule]** problemen bij het upgraden vanaf Adobe Commerce versies &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** problemen met labels bij upgrades van versies &lt; 2.4.5

De **[!UICONTROL salesRule]** label staging-functionaliteit is geïntroduceerd in Adobe Commerce [2.4.5.](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Deze wijziging kan mogelijk problemen veroorzaken wanneer u een upgrade uitvoert van Adobe Commerce &lt; 2.4.5 naar een willekeurige versie >= 2.4.5. Na de upgrade is het mogelijk dat **[!UICONTROL salesRule]** de labels komen niet overeen. Als u dit probleem wilt verhelpen, moet u direct na de upgrade een patch toepassen op een nieuwere Adobe Commerce-versie.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur &lt; 2.4.5

## Reparatie

Gebruik de volgende bijgevoegde patch:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Hoe de pleister aanbrengen

1. Voer de stappen uit in [Een upgrade uitvoeren](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) in de handleiding van Commerce.
1. Plaats de bijgevoegde patch voor de **[!UICONTROL Update metadata]** fase.
(U kunt de pleister ook aanbrengen nadat u de **[!UICONTROL Update metadata]** fase maar dan moet u lopen `bin/magento setup:upgrade` nogmaals).
1. Ga verder met de overige stappen in [Een upgrade uitvoeren](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
