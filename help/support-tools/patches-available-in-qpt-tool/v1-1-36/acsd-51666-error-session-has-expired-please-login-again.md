---
title: 'ACSD-51666: Fout "De sessie is verlopen. Meld u opnieuw aan." nadat u zich hebt aangemeld'
description: Pas de ACSD-51666-patch toe om het Adobe Commerce-probleem op te lossen waarbij de fout *De sessie is verlopen. Meld u opnieuw aan.* treedt op nadat u zich hebt aangemeld.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666: Fout *De zitting is verlopen, gelieve login opnieuw.* nadat u zich hebt aangemeld

ACSD-51666 flardmoeilijke situatie de kwestie waar de fout *de zitting is verlopen, gelieve login opnieuw.* treedt op nadat u zich hebt aangemeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-5166. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U krijgt de fout *de zitting is verlopen, gelieve login opnieuw.* wanneer u zich probeert aan te melden met het nieuwe wachtwoord van een apparaat nadat u het wachtwoord opnieuw hebt ingesteld op een ander apparaat. Het gebeurt slechts als er een extra Ajax- verzoek op de pagina is die door een douanemodule wordt toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Installeer een aangepaste module die een Ajax-aanvraag toevoegt op elke pagina in de winkel.
1. Maak een nieuw account.
1. Log uit en ga terug naar de aanmeldingspagina.
1. Open de *vergeten verbinding van het Wachtwoord* in verschillende browser en verzend het *Wachtwoord van het Terugstellen* e-mail.
1. Open de e-mail met het wachtwoord voor opnieuw instellen in de eerste browser en stel het nieuwe wachtwoord in.
1. Meld u aan in de tweede browser.

<u> Verwachte resultaten </u>:

U kunt zich met succes aanmelden bij de eerste poging.

<u> Ware resultaten </u>:

* U ziet *de zitting is verlopen, gelieve login opnieuw.* error.
* U bent niet aangemeld en u wordt omgeleid naar de startpagina.
* De tweede poging tot aanmelden is geslaagd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
