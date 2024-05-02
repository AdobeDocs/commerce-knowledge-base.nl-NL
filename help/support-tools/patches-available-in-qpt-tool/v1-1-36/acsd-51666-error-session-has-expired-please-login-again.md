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

# ACSD-51666: Fout *De sessie is verlopen. Meld u opnieuw aan.* nadat u zich hebt aangemeld

De ACSD-51666-patch verhelpt het probleem waarbij de fout optreedt *De sessie is verlopen. Meld u opnieuw aan.* treedt op nadat u zich hebt aangemeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 is geïnstalleerd. De patch-id is ACSD-5166. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout verschijnt *De sessie is verlopen. Meld u opnieuw aan.* wanneer u zich probeert aan te melden met het nieuwe wachtwoord van een apparaat nadat u het wachtwoord opnieuw hebt ingesteld op een ander apparaat. Het gebeurt slechts als er een extra Ajax- verzoek op de pagina is die door een douanemodule wordt toegevoegd.

<u>Stappen om te reproduceren</u>:

1. Installeer een aangepaste module die een Ajax-aanvraag toevoegt op elke pagina in de winkel.
1. Maak een nieuw account.
1. Log uit en ga terug naar de aanmeldingspagina.
1. Open de *Wachtwoord vergeten* een koppeling in een andere browser maken en de *Wachtwoord opnieuw instellen* e-mail.
1. Open de e-mail met het wachtwoord voor opnieuw instellen in de eerste browser en stel het nieuwe wachtwoord in.
1. Meld u aan in de tweede browser.

<u>Verwachte resultaten</u>:

U kunt zich met succes aanmelden bij de eerste poging.

<u>Werkelijke resultaten</u>:

* U ziet de *De sessie is verlopen. Meld u opnieuw aan.* fout.
* U bent niet aangemeld en u wordt omgeleid naar de startpagina.
* De tweede poging tot aanmelden is geslaagd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
