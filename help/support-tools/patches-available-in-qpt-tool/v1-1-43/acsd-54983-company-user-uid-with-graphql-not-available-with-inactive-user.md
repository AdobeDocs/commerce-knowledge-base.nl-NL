---
title: 'ACSD-54983: Bedrijfs-gebruikers-UID met GraphQL niet beschikbaar bij inactieve gebruiker'
description: Pas de ACSD-54983-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het niet mogelijk is om de UID van de bedrijfsgebruiker op te halen met GraphQL-verzoek wanneer de gebruikersstatus is ingesteld op inactief.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: Bedrijfs-UID met GraphQL niet beschikbaar bij inactieve gebruiker

De ACSD-54983-patch verhelpt het probleem waarbij het niet mogelijk is om de UID van de bedrijfsgebruiker op te halen bij een GraphQL-aanvraag als de gebruikersstatus is ingesteld op inactief. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-54983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan de UID van de bedrijfsgebruiker niet ophalen met GraphQL-aanvraag als de gebruikersstatus is ingesteld op inactief.

<u>Stappen om te reproduceren</u>:

1. Maak een bedrijf met een beheerder. Bijvoorbeeld company@test.com.
1. Maak een nieuwe klant.
1. Wijs de nieuwe klant aan een bedrijf toe.
1. Get a **[!UICONTROL company admin token]**.
1. Met de **[!UICONTROL company admin token]**, haalt u de bedrijfsstructuur op. Zie [De bedrijfsstructuur retourneren](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) in onze ontwikkelaarsdocumentatie.
1. De reactie bevat alleen *ACTIEF* klanten met hun id&#39;s.
1. Werk de bedrijfgebruiker bij aan *INACTIEF*.
1. Haal de bedrijfsstructuur opnieuw op.

<u>Verwachte resultaten</u>:

Het is mogelijk om UID van de bedrijfgebruiker te krijgen wanneer de status aan inactief wordt geplaatst.

<u>Werkelijke resultaten</u>:

De niet-actieve klanten staan niet in de lijst. Kan de UID van de bedrijfsgebruiker niet ophalen wanneer de status is ingesteld op inactief.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
