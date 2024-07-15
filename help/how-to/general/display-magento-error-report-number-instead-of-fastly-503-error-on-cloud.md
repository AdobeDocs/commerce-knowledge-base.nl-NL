---
title: Geef Adobe Commerce-foutrapportnummer weer in plaats van Fastly 503-fout
description: 'Standaard worden met Snelheid alle Adobe Commerce-fouten verborgen achter de fout **503 Service niet beschikbaar**. Als u het rapportnummer van het Adobe Commerce-foutenlogboek wilt weergeven (zodat u het kunt vinden in logboeken en de foutdetails kunt zien), opent u de website zonder dat u snel de volgende stappen uitvoert:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Geef Adobe Commerce-foutrapportnummer weer in plaats van Fastly 503-fout

Door gebrek, verbergt de Fastly alle fouten van Adobe Commerce achter de **503 niet beschikbare** fout van de Dienst. Als u het rapportnummer van het Adobe Commerce-foutenlogboek wilt weergeven (zodat u het kunt vinden in logboeken en de foutdetails kunt zien), opent u de website zonder dat u snel de volgende stappen uitvoert:

1. Voeg het domein en IP-adres van uw toepassing toe aan het hostbestand op uw lokale computer.
1. Wis de browsercache en cookies (of schakel over naar de incognitomodus).
1. Open opnieuw de website van uw winkel om de Adobe Commerce-fout te zien.

Als u de authentieke Adobe Commerce-fout en het nummer van het foutrapport ziet, worden mogelijk gegevens in het foutrapportbestand weergegeven door de volgende stappen uit te voeren:

1. SSH naar het betrokken milieu. Verwijs naar [ SSH aan een milieu ](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) in onze ontwikkelaarsdocumentatie.
1. Zoek het `./var/report/{error_number}` -bestand.

## Toepassingsdomein en IP-adres toevoegen aan het hostbestand: gedetailleerde stappen

1. Controleer de server-IP van uw winkel door de opdracht `nslookup` uit te voeren op de opdrachtregel op uw lokale computer:
   * Pro-architectuurgebruikers (Staging- en Productieomgevingen):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Gebruikers van de starterarchitectuur (alle omgevingen); Pro-architectuurgebruikers (integratieomgeving):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Voeg uw opslagdomein en IP van de toepassingsserver aan het gastheerdossier op uw lokale computer toe gebruikend het volgende formaat:

```
{server_IP} {store_domain}
```
