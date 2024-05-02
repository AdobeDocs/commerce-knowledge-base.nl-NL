---
title: "ACSD-51907: gebruikers met beperkte beheerdersrechten kunnen geen creditnota voor offline terugbetaling maken"
description: Pas de ACSD-51907-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gebruiker met beperkte beheerdersrechten geen creditmemo met een offlinerestitutie kan maken.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: gebruikers met beperkte beheerdersrechten kunnen geen creditnota voor offline restitutie maken

De ACSD-51907-patch verhelpt het prestatieprobleem waarbij een gebruiker met beperkte beheerdersrechten geen creditmemo met een offline restitutie kan maken. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51907. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte gebruikers van beheerders kunnen geen creditnota met een off-line terugbetaling tot stand brengen.

<u>Stappen om te reproduceren</u>:

1. Een **klant** op de standaardwebsite.
1. Maken **nieuwe website** met betrekking tot *winkel* en *winkelweergave*.
1. Standaardwebsite instellen op nieuwe website, caches wissen.
1. Configuratie klant wijzigen: **Beheerder** > **Winkel** > **Configuratie** > **Klanten** > **Klantconfiguratie** > **Klantaccounts delen = Algemeen**.
1. Nieuwe beheerdersrol maken met het rolbereik ingesteld op nieuwe gemaakte website *(alleen toegang tot verkoopgegevens)* in **Beheerder** > **Systeem** > **Machtigingen**.
1. Maak een nieuw beheerdersaccount met deze rol.
1. Nieuwe bestelling maken met de online betalingsmethode *(bijvoorbeeld Auth.net of PayPal)*.
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Ga naar **Verkoop** > **Orders** > dan **weergavepagina bestellen**.
1. Maak een factuur.
1. Navigeer naar het tabblad Facturen.
1. Klikken op **Factuur**.
1. Klikken op **[!UICONTROL Credit Memo]**.
1. Controleer de **[!UICONTROL Refund to Store Credit]** selectievakje, tekstveld bij instellen op *1* waarde.
1. Klik op de knop **[!UICONTROL Refund Offline]** knop.

<u>Verwachte resultaten</u>:

De creditmemo wordt gemaakt, en *$1* wordt teruggestort op het winkelkrediet.

<u>Werkelijke resultaten</u>:

Het foutbericht, *Er zijn meer machtigingen nodig om dit item weer te geven* wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
