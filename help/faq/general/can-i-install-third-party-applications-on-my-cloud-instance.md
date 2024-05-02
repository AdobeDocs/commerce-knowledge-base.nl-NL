---
title: Kan ik toepassingen van derden installeren op mijn cloudexemplaar?
description: Nee. Het is niet toegestaan apps van derden (zoals WordPress of Drupal) op de Adobe Commerce te installeren op cloudinframinframeservers. U moet dergelijke toepassingen hosten op externe servers.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Kan ik toepassingen van derden installeren op mijn cloudexemplaar?

Nee. Het is niet toegestaan apps van derden (zoals WordPress of Drupal) op de Adobe Commerce te installeren op cloudinframinframeservers. U moet dergelijke toepassingen hosten op externe servers.

## Redenen

### Serviceovereenkomst

De Adobe Commerce on cloud Infrastructure Edition [Serviceovereenkomst](https://magento.com/legal/terms/cloud-terms) In artikel 18 wordt het volgende vermeld:

> De klant stemt ermee in dat Adobe Commerce en de Service niet worden gebruikt voor het hosten van andere softwaretoepassingen van derden die niet rechtstreeks afhankelijk zijn van de Software.

Als cloudoplossing neemt Adobe de volledige verantwoordelijkheid voor de beveiliging van uw server. Om hoge veiligheid te garanderen, staan wij slechts het ontvangen van de toepassing van Adobe Commerce op de specifieke wolkenserver toe.

### PCI-compatibiliteit

Als een PCI-gecertificeerde Level 1 Solution Provider moet Adobe Commerce op cloudinfrastructuur de PCI Data Security Standard volgen en ervoor zorgen dat:

>... Beveiligde systemen en toepassingen ontwikkelen en onderhouden
> ([Aanpak van Adobe aan naleving PCI](https://magento.com/pci-compliance) Eis 6, een programma voor kwetsbaarheidsbeheer onderhouden)

Aangezien Adobe de PCI-compatibiliteit van toepassingen van derden niet kan garanderen, is het installeren van dergelijke toepassingen op cloudservers niet toegestaan.

## Tip: gebruik Commerce Marketplace-extensies voor betere integratie

Om de integratie van uw Adobe Commerce op de toepassing van de wolkeninfrastructuur met de derdeoplossingen te verbeteren die op externe servers worden ontvangen, moedigen wij u aan om te gebruiken [Commerce Marketplace](https://marketplace.magento.com) extensies die geschikt zijn voor uw doel.
