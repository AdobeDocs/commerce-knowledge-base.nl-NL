---
title: Leeg pagina- of omleidingsfout bij toegang tot winkel of Commerce-beheerder
description: Dit artikel biedt een oplossing voor dit probleem wanneer u toegang krijgt tot Adobe Commerce-winkel of -back-end en een lege pagina of omleidingslus krijgt.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Leeg pagina- of omleidingsfout bij toegang tot winkel of Commerce-beheerder

Dit artikel biedt een oplossing voor dit probleem wanneer u toegang krijgt tot Adobe Commerce-winkel of -back-end en een lege pagina of omleidingslus krijgt.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies
* Adobe Commerce op locatie, alle versies
* Magento Open Source, alle versies

## Probleem

<u> Stappen om te reproduceren </u>

Open een winkel- of beheerpagina.

<u> Verwacht resultaat </u>

De pagina wordt geopend.

<u> Werkelijk resultaat </u>

De pagina is leeg of toont *&quot;Deze webpage heeft een herleidingslijn&quot;* foutenmelding.

## Oorzaak

Een van de meest waarschijnlijke redenen voor deze uitgave is dat Adobe Commerce is ingesteld op omleiding van een onveilige URL naar een beveiligde URL, maar dat een onveilige URL wordt opgegeven als de waarde voor de veilige URL-instelling.

Om de kwestie te bevestigen, moet u de waarde van de veilige verbinding verbeteren.

## Oplossing

Ga als volgt te werk om ervoor te zorgen dat dit de oorzaak van het probleem is:

1. Controleer de waarde `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (als u een probleem met de blanco-/lusbewerking hebt in Admin) of `web/secure/use_in_frontend` (als u een probleem met de blanco-/lusbewerking hebt op de winkelvoorzijde) in de `'core_config_data'` DB-tabel.
   * Als `web/secure/enable_upgrade_insecure` is ingesteld op &quot;1&quot;, wordt Adobe Commerce ingesteld op het toevoegen van de responsheader `Content-Security-Policy: upgrade-insecure-requests` , waarmee browsers wordt geïnstrueerd HTTPS te gebruiken en alle query&#39;s die via HTTP worden verzonden, worden doorgestuurd
naar HTTPS, voor zowel Admin als storefront.
   * Als `web/secure/use_in_adminhtml` is ingesteld op &quot;1&quot;, retourneert Adobe Commerce HTTPS-omleidingen voor alle HTTP-aanvragen voor de beheerpagina&#39;s.
   * Als `web/secure/use_in_frontend` is ingesteld op &quot;1&quot;, retourneert Adobe Commerce HTTPS omleidingen voor alle HTTP-aanvragen voor de winkelvoorpagina&#39;s.
1. Controleer de waarden `web/secure/base_url` en `web/unsecure/base_url` in de tabel `'core_config_data'` . Als beide beginnen met    `http` , moet u de waarde &quot;secure&quot; corrigeren.

Probleem verhelpen:

1. De waarde instellen op `https` for `web/secure/base_url.`
1. Voor de uit te voeren veranderingen, schoon het configuratiecache door het volgende bevel in werking te stellen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
