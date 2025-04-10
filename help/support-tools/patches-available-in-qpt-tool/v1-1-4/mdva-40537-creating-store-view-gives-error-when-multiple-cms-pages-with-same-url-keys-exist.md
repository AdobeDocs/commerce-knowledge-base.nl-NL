---
title: 'MDVA-40537: Het maken van een winkelweergave geeft een fout weer wanneer meerdere CMS-pagina''s dezelfde URL-sleutel hebben.'
description: De patch MDVA-40537 verhelpt het probleem waarbij gebruikers een fout krijgen bij het maken van een winkelweergave als meerdere CMS-pagina's dezelfde URL-sleutel hebben. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40537. De kwestie is opgelost in Adobe Commerce 2.4.1.
exl-id: d92400c9-0c5a-4416-820d-99ab4ba34003
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-40537: Het maken van een winkelweergave geeft een fout weer wanneer meerdere CMS-pagina&#39;s dezelfde URL-sleutel hebben.

De patch MDVA-40537 verhelpt het probleem waarbij gebruikers een fout krijgen bij het maken van een winkelweergave als meerdere CMS-pagina&#39;s dezelfde URL-sleutel hebben. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4 geïnstalleerd is. De patch-id is MDVA-40537. De kwestie is opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.


## Probleem

Gebruikers krijgen een fout wanneer ze een winkelweergave maken als meerdere CMS-pagina&#39;s dezelfde URL-sleutel hebben.

<u> Stappen om </u> te reproduceren:

1. Ga naar het **Comité Admin** > **Slaat** > **Alle Sporen** op en creeer twee opslagmeningen.

   ```sql
   Name: German
   Code: german
   Status: Enabled
   ```

   ```sql
   Name: French
   Code: french
   Status: Enabled
   ```

1. Ga naar het **Comité Admin** > **Inhoud** > **Pagina&#39;s** en creeer twee pagina&#39;s.

   ```sql
   Page Title: About Us
   URL Key: about-us
   Store View: French
   ```

   ```sql
   Page Title: About Us
   URL Key: about-us
   Store View: German
   ```

1. Ga naar het **Comité Admin** > **Slaat** > **Alle opslag** op en creeer een nieuwe opslagmening.

   ```sql
   Name: Spanish
   Code: spanish
   Status: Enabled
   ```

<u> Verwachte resultaten </u>:

De winkelweergave is gemaakt.

<u> Ware resultaten </u>:

Het volgende foutenbericht wordt getoond: *iets ging verkeerd terwijl het bewaren. Controleer het foutenlogboek.* Het logbestand bevat een uitzondering zoals:

```sql
Exception message: SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'about-us-4' for key 'URL_REWRITE_REQUEST_PATH_STORE_ID', query was: INSERT  INTO }}url_rewrite{{ (}}redirect_type{{,}}is_autogenerated{{,}}metadata{{,}}description{{,}}store_id{{,}}entity_type{{,}}entity_id{{,}}request_path{{,}}target_path{{) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?), (?, ?, ?, ?, ?, ?, ?, ?, ?), (?, ?, ?, ?, ?, ?, ?, ?, ?), (?, ?, ?, ?, ?, ?, ?, ?, ?), (?, ?, ?, ?, ?, ?, ?, ?, ?), (?, ?, ?, ?, ?, ?, ?, ?, ?)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
