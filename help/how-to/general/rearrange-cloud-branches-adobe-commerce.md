---
title: Kolomvertakkingen opnieuw rangschikken op Adobe Commerce
description: In dit artikel worden de stappen beschreven die u kunt uitvoeren om vertakkingen in de cloud opnieuw te rangschikken op Adobe Commerce als deze niet volgens de juiste hiërarchie zijn ingedeeld. Als u de vertakkingen niet in correcte hiërarchie hebt georganiseerd, zult u niet aan de correcte oudertak kunnen samenvoegen - het zal naar de bestaande oudertak gaan.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Kolomvertakkingen opnieuw rangschikken op Adobe Commerce

In dit artikel worden de stappen beschreven die u kunt uitvoeren om vertakkingen in de cloud opnieuw te rangschikken op Adobe Commerce als deze niet volgens de juiste hiërarchie zijn ingedeeld. Als u de vertakkingen niet in correcte hiërarchie hebt georganiseerd, zult u niet aan de correcte oudertak kunnen samenvoegen - het zal naar de bestaande oudertak gaan.

## Betrokken producten en versies:

* Adobe Commerce on cloud Infrastructure, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organisatie van wolkenvertakkingen

De juiste hiërarchische organisatie voor uw vertakkingen is:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Oplossing voor onjuiste organisatie van wolkenvertakkingen

Zo rangschikt u vertakkingen in de cloud:

1. U moet de [[!DNL Super User] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) rol hebben.
1. Installeer de magento-cloud [!DNL CLI] (als u dat nog niet hebt gedaan).
1. Voer de volgende opdracht uit voor de vertakkingen die moeten worden verplaatst:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Opmerking: u kunt de bovenliggende vertakking opgeven wanneer u een nieuwe vertakking maakt. Voor stappen, verwijs naar [ het Beginnen van Begin creërend takken ](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted) in onze ontwikkelaarsdocumentatie.

U kunt een nieuwe omgevingsvertakking maken met de omgevingsopdracht `branch <environment-name> <parent-environment-ID>` magento-cloud.

Het kan enige extra tijd duren om een nieuwe omgevingsvertakking te maken en te activeren.

## Gerelateerde lezing

[ beheer takken met  [!DNL CLI] ](https://devdocs.magento.com/cloud/env/environments-start.html) in onze ontwikkelaarsdocumentatie.
