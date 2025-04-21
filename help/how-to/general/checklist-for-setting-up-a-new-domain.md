---
title: Checklist voor vestiging een nieuw  [!DNL domain]
description: Dit is een controlelijst van hoe te opstelling a nieuw  [!DNL domain]  in Adobe Commerce op wolkeninfrastructuur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: f7b246088e3580922bd3389b2992e5dd8f97ff7a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Controlelijst voor het instellen van een nieuwe versie [!DNL domain]

In deze checklist wordt uitgelegd hoe u een nieuwe [!DNL domain] -versie instelt in Adobe Commerce op cloudinfrastructuur. Het is van toepassing of u een nieuw domein toevoegt of huidige vervangt. Het is ook van toepassing na het krijgen van een nieuwe het Staging milieu (zie Stap 4).

## Betrokken producten en versies

Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Hoe te opstelling een nieuw domein

### Stap 1 - Is dit voor [!DNL Integration, Staging], of [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] worden niet ondersteund. U moet deze methode in plaats daarvan gebruiken: [ Opstelling veelvoudige websites of opslag: Vorm lokale installatie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikersgids.
* **[!DNL Staging]**: Ga naar **Stap 2**.
* **[!DNL Production]**: Ga naar **Stap 3**.

### Stap 2 - [!DNL Staging environment] : bevindt u zich op [!DNL Pro] of [!DNL Starter] ?

* **[!DNL Pro]**: **leg een verzoek** voor om het domein aan [!DNL Fastly, Nginx] toe te voegen, en vorm [!DNL SSL certificate] (evenals [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, [ werk de  [!DNL DNS]  configuratie met  [!DNL development settings] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) bij.

>[!NOTE]
>
>U kunt de nieuwe [!DNL domain] aan [!DNL Fastly] zelf toevoegen door de configuratie in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** bij te werken, zoals in [[!DNL Manage domains] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in de gebruikershandleiding.
>
>Als u het domein niet kunt toevoegen, kan dit aan een van de volgende redenen zijn te wijten:
>
>1. U migreert het domein naar de wolkenomgeving, die in uw eigen [!DNL Fastly] dienst is gevormd. In dit geval dient u een verzoek in en vraagt u om delegatie van het domein.
>1. U migreert het domein van Starter naar Pro. In dat geval dient de Commissie een verzoek om verdere bijstand in.

* **[!DNL Starter]**: [!DNL Custom domains] worden niet ondersteund in de testomgeving.

### Stap 3 - [!DNL Production environment] : bevindt u zich op [!DNL Pro] of [!DNL Starter] ?

* **[!DNL Pro]**: **leg een verzoek** voor om het domein aan [!DNL Fastly, Nginx] toe te voegen, en vorm [!DNL SSL certificate] (als [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, blijf aan **Stap 4**.

>[!NOTE]
>
>U kunt de nieuwe [!DNL domain] aan [!DNL Fastly] zelf toevoegen door de configuratie in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) bij te werken in de gebruikershandleiding.
>
>
>Als u het domein niet kunt toevoegen, kan dit aan een van de volgende redenen zijn te wijten:
>
>1. U migreert het domein van op-gebouw aan het wolkenmilieu, dat in uw eigen [!DNL Fastly] dienst is gevormd. In dit geval dient u een verzoek in en vraagt u om delegatie van het domein.
>1. U migreert het domein van Starter naar Pro. In dat geval dient de Commissie een verzoek om verdere bijstand in.

* **[!DNL Starter]**: Voeg [!DNL domain] aan uw project in het **[!DNL Domains]** lusje toe, dan **verzend een verzoek** om **[!DNL ACME Challenge Key]** voor [!DNL SSL certificate] te verstrekken.

### Stap 4 - Is de [!DNL domain] live?

* **JA**: [ werk de  [!DNL DNS]  configuratie met [!UICONTROL production] montages ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings) bij.
* **GEEN**: [ werk de  [!DNL DNS]  configuratie met [!UICONTROL development] montages ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) bij.

## Gerelateerde lezing

* [ Opstelling veelvoudige websites of opslag: voeg Nieuw  [!DNL Domains] ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikersgids toe.
* [ Plaats niet toegankelijk toe te schrijven aan oorsprong het camoufleren ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
