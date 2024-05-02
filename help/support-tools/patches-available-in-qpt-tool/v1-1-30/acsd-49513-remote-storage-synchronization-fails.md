---
title: 'ACSD-49513: Synchronisatie van externe opslag mislukt'
description: Pas de ACSD-49513-patch toe om het Adobe Commerce-probleem op te lossen waarbij de synchronisatie van de externe opslag mislukt als gevolg van 0-byte bestanden.
exl-id: fce5f60f-d21f-40cd-8d8a-a1a26e0fbe75
feature: Iaas, Storage
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-49513: Synchronisatie van externe opslag mislukt vanwege bestanden van 0 byte

De ACSD-49513-patch verhelpt het probleem waarbij de synchronisatie van de externe opslag mislukt als gevolg van bestanden van 0 byte. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-49513. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De synchronisatie van de externe opslag mislukt vanwege bestanden van 0 byte.

<u>Stappen om te reproduceren</u>:

1. Configureer de AWS S3 als externe opslag.
1. Uitvoeren `[bin/magento remote-storage:sync]` om ervoor te zorgen dat de synchronisatie aan het begin behoorlijk werkt.
1. Een bestand van 0 byte maken in het dialoogvenster `[pub/media]`.
1. Uitvoeren `[bin/magento remote-storage:sync]` opnieuw.

<u>Verwachte resultaten</u>:

Aangezien de AWS S3 0-byte bestanden accepteert op de S3 Direct-push, is er geen fout.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
