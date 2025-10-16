---
title: Checklist voor vestiging een nieuw  [!DNL domain]
description: Dit is een controlelijst van hoe te opstelling a nieuw  [!DNL domain]  in Adobe Commerce op wolkeninfrastructuur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Controlelijst voor het instellen van een nieuwe versie [!DNL domain]

In deze checklist wordt uitgelegd hoe u een nieuwe [!DNL domain] -versie instelt in Adobe Commerce op cloudinfrastructuur. Het is van toepassing of u een nieuw domein toevoegt of huidige vervangt. Het is ook van toepassing na het krijgen van een nieuwe het Staging milieu (zie Stap 4).

## Betrokken producten en versies

Adobe Commerce op wolkeninfrastructuur, [&#x200B; alle gesteunde versies &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Hoe te opstelling een nieuw domein

>[!NOTE]
>
>Controleer voordat u verdergaat met instellen van het domein of:
>
>Alle basis-URL&#39;s zijn geconfigureerd voor het gebruik van HTTPS onder **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** , met het bereik van de juiste website- of opslagweergave.
>&#x200B;> [De kracht TLS &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996) wordt toegelaten om al verkeer van HTTP aan HTTPS over uw plaats van Adobe Commerce op wolkeninfrastructuur om te leiden.

### Stap 1 - Is dit voor [!DNL Integration, Staging], of [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] worden niet ondersteund. U moet deze methode in plaats daarvan gebruiken: [&#x200B; Opstelling veelvoudige websites of opslag: Vorm lokale installatie &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikersgids.
* **[!DNL Staging]**: Ga naar **Stap 2**.
* **[!DNL Production]**: Ga naar **Stap 3**.

### Stap 2 - [!DNL Staging environment] : bevindt u zich op [!DNL Pro] of [!DNL Starter] ?

* **[!DNL Pro]**: **leg een verzoek** voor om het domein aan [!DNL Fastly, Nginx] toe te voegen, en vorm [!DNL SSL certificate] (evenals [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, [&#x200B; werk de  [!DNL DNS]  configuratie met  [!DNL development settings] &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) bij.

>[!NOTE]
>
>Voor PRO-architectuur moet bij het toevoegen van een nieuw domein een supportverzoek worden ingediend bij Adobe Commerce. Hoewel sommige klanten in staat kunnen zijn om snel handmatig via de Admin Console te configureren, geldt dit alleen in beperkte gevallen, bijvoorbeeld wanneer het domein niet is gekoppeld aan een andere Fastly-service of een ander Fastly-project. Nochtans, is de configuratie Nginx altijd vereist, en deze stap moet door Adobe worden behandeld. Wegens dit, is de geadviseerde en betrouwbaarste benadering a [&#x200B; steunkaartje &#x200B;](https://experienceleague.adobe.com/home?support-tab=home#support) voor te leggen en Adobe het volledige proces van de domeinopstelling te laten beheren.


* **[!DNL Starter]**: [!DNL Custom domains] worden niet ondersteund in de testomgeving.

### Stap 3 - [!DNL Production environment] : bevindt u zich op [!DNL Pro] of [!DNL Starter] ?

* **[!DNL Pro]**: **leg een verzoek** voor om het domein aan [!DNL Fastly, Nginx] toe te voegen, en vorm [!DNL SSL certificate] (als [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, blijf aan **Stap 4**.

>[!NOTE]
>
>U kunt de nieuwe [!DNL domain] aan [!DNL Fastly] zelf toevoegen door de configuratie in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains] &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) bij te werken in de gebruikershandleiding.
>
>
>Als u het domein niet kunt toevoegen, kan dit aan een van de volgende redenen zijn te wijten:
>
>1. U migreert het domein van op-gebouw aan het wolkenmilieu, dat in uw eigen [!DNL Fastly] dienst is gevormd. In dit geval dient u een verzoek in en vraagt u om delegatie van het domein.
>1. U migreert het domein van Starter naar Pro. In dat geval dient de Commissie een verzoek om verdere bijstand in.

* **[!DNL Starter]**: Voeg [!DNL domain] aan uw project in het **[!DNL Domains]** lusje toe, dan **verzend een verzoek** om **[!DNL ACME Challenge Key]** voor [!DNL SSL certificate] te verstrekken.

### Stap 4 - Is de [!DNL domain] live?

* **JA**: [&#x200B; werk de  [!DNL DNS]  configuratie met [!UICONTROL production] montages &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings) bij.
* **GEEN**: [&#x200B; werk de  [!DNL DNS]  configuratie met [!UICONTROL development] montages &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) bij.

### Stap 5 - Zijn domeinomleidingen geconfigureerd in `magento-vars.php` ?

Nadat het domein is gevormd, moet u [&#x200B; de variabelen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) in het `magento-vars.php` dossier wijzigen om het domein aan de aangewezen website/opslag URL te leiden.

### Stap 6 - Is de [!DNL domain] configuratie geverifieerd?

Als u nieuwe winkels, opslaggroepen en websites hebt toegevoegd in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** voor de nieuwe domeinen, controleert u of de volgende secties worden weergegeven in uw `app/etc/config.php` -bestand, bijvoorbeeld:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Dit betekent dat u opstelling [&#x200B; SCD op Bouwstijl &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) door het `config:dump` bevel in het `ece-tools` pakket in het verleden in werking te stellen hebt.

Als de nieuwe winkel of website die u hebt gemaakt, niet wordt weergegeven in het `app/etc/config.php` -bestand, moet u de opdracht opnieuw uitvoeren om het `config.php` -bestand te synchroniseren met de wijzigingen in uw database, en vervolgens het `config.php` -bestand toewijzen en opnieuw implementeren. Dit is bedoeld om de implementatie van statische inhoud voor de nieuwe winkel/website(s) naar de juiste bestandspaden te vergemakkelijken.

## Gerelateerde lezing

* [&#x200B; Opstelling veelvoudige websites of opslag: voeg Nieuw  [!DNL Domains] &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikersgids toe.
* [&#x200B; Plaats niet toegankelijk toe te schrijven aan oorsprong het camoufleren &#x200B;](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
