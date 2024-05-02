---
title: 'ACSD-50336: E-mails met productwaarschuwing niet verzonden'
description: Pas de ACSD-50336-patch toe om het Adobe Commerce-probleem op te lossen wanneer de e-mails met productwaarschuwingen niet worden verzonden wanneer een product weer in voorraad is of de prijs wordt gewijzigd.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: e-mails met productwaarschuwing niet verzonden

De ACSD-50336-patch verhelpt het probleem dat er geen e-mails met productwaarschuwingen worden verzonden wanneer een product weer in voorraad is of de prijs wordt gewijzigd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-50336. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden geen e-mailberichten verzonden wanneer een product weer in voorraad is of de prijs is gewijzigd.

<u>Vereisten</u>:

Stel productwaarschuwingen in voor wanneer een product weer aan voorraad wordt toegevoegd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als klant op de winkel.
1. Open een product dat niet in voorraad is.
1. Abonneren om een bericht te ontvangen wanneer het product is *back-up*.
1. Het product bijwerken vanaf [!UICONTROL Admin] te worden _back-up_.

<u>Verwachte resultaten</u>:

Een e-mailmelding over het product dat *back-up* wordt naar de klant verzonden.

<u>Werkelijke resultaten</u>:

De klant ontvangt geen e-mailbericht over het product dat wordt *back-up*. De volgende fout wordt in het logbestand weergegeven:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
