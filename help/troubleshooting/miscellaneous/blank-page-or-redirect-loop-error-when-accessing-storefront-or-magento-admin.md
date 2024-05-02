---
title: Leeg pagina- of omleidingsfout bij toegang tot winkel of Commerce-beheerder
description: Dit artikel biedt een oplossing voor dit probleem wanneer u toegang krijgt tot Adobe Commerce-winkel of -back-end en een lege pagina of omleidingslus krijgt.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Leeg pagina- of omleidingsfout bij toegang tot winkel of Commerce-beheerder

Dit artikel biedt een oplossing voor dit probleem wanneer u toegang krijgt tot Adobe Commerce-winkel of -back-end en een lege pagina of omleidingslus krijgt.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies
* Adobe Commerce op locatie, alle versies
* Magento Open Source, alle versies

## Probleem

<u>Stappen om te reproduceren</u>

Open een winkel- of beheerpagina.

<u>Verwacht resultaat</u>

De pagina wordt geopend.

<u>Werkelijk resultaat</u>

De pagina is leeg of geeft de *&quot;Deze webpagina heeft een omleidingslus&quot;* foutbericht.

## Oorzaak

Een van de meest waarschijnlijke redenen voor deze uitgave is dat Adobe Commerce is ingesteld op omleiding van een onveilige URL naar een beveiligde URL, maar dat een onveilige URL wordt opgegeven als de waarde voor de veilige URL-instelling.

Om de kwestie te bevestigen, moet u de waarde van de veilige verbinding verbeteren.

## Oplossing

Ga als volgt te werk om ervoor te zorgen dat dit de oorzaak van het probleem is:

1. Controleer de `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (als u een probleem hebt met de blanco-/lusomleiding in Admin) of `web/secure/use_in_frontend` (als u de uitgave voor het omleiden van de blanco/lus op de winkelvoorzijde hebt) in de `'core_config_data'` DB-tabel.
   * Indien `web/secure/enable_upgrade_insecure` is ingesteld op &quot;1&quot;, en Adobe Commerce is ingesteld op het toevoegen van de antwoordheader `Content-Security-Policy: upgrade-insecure-requests`, waardoor browsers de instructie krijgen HTTPS te gebruiken, waarbij alle query&#39;s die via HTTP naar HTTPS worden verzonden, voor zowel Admin als storefront worden doorgestuurd.
   * Indien `web/secure/use_in_adminhtml` is ingesteld op &quot;1&quot;, Adobe Commerce retourneert HTTPS-omleidingen voor alle HTTP-aanvragen voor de beheerpagina&#39;s.
   * Indien `web/secure/use_in_frontend` is ingesteld op &quot;1&quot;, Adobe Commerce retourneert HTTPS-omleidingen voor alle HTTP-aanvragen voor de winkelvoorpagina&#39;s.
1. Controleer de `web/secure/base_url` en `web/unsecure/base_url` waarden in de `'core_config_data'` tabel. Als beide beginnen met    `http`, dan moet u de &quot;veilige&quot;waarde verbeteren.

Probleem verhelpen:

1. Stel de waarde in die begint met `https` for `web/secure/base_url.`
1. Voor de uit te voeren veranderingen, schoon het configuratiecache door het volgende bevel in werking te stellen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
