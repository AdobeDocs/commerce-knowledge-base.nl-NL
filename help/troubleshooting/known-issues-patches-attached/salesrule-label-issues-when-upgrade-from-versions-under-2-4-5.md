---
title: '[!UICONTROL salesRule] geeft labels aan bij upgrades van versies &lt; 2.4.5'
description: Pas een patch toe om de **[!UICONTROL salesRule]** problemen op te lossen wanneer u een upgrade uitvoert van Adobe Commerce versies &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** geeft een label bij upgrades van versies &lt; 2.4.5

De **[!UICONTROL salesRule]** functionaliteit van het etiketopvoeren werd geïntroduceerd in Adobe Commerce [ 2.4.5 ](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Deze wijziging kan mogelijk problemen veroorzaken wanneer u een upgrade uitvoert van Adobe Commerce &lt; 2.4.5 naar een willekeurige versie >= 2.4.5. Na de upgrade is het mogelijk dat **[!UICONTROL salesRule]** -labels niet overeenkomen. Als u dit probleem wilt verhelpen, moet u direct na de upgrade een patch toepassen op een nieuwere Adobe Commerce-versie.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur &lt; 2.4.5

## Reparatie

Gebruik de volgende bijgevoegde patch:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Hoe de pleister aanbrengen

1. Volg de stappen in [ een verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) in de gids van Commerce uitvoeren.
1. Pas de bijgevoegde patch toe vóór de **[!UICONTROL Update metadata]** -fase.
(U kunt de patch ook toepassen nadat u de **[!UICONTROL Update metadata]** -fase hebt voltooid, maar dan moet u `bin/magento setup:upgrade` opnieuw uitvoeren.)
1. Ga met de rest stappen in [ te werk voeren een verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) uit.
