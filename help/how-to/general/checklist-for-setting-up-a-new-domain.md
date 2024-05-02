---
title: Controlelijst voor het instellen van een nieuwe [!DNL domain]
description: Dit is een controlelijst voor het instellen van een nieuwe [!DNL domain] in Adobe Commerce over cloudinfrastructuur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: cc3dc1e3f9c8f98370ce5db125b402d4c1dfbd6f
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Controlelijst voor het instellen van een nieuwe [!DNL domain]

Dit is een controlelijst voor het instellen van een nieuwe [!DNL domain] in Adobe Commerce over cloudinfrastructuur. Het is van toepassing, ongeacht of u een nieuw domein wilt toevoegen of het huidige domein wilt vervangen door een nieuw domein.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Hoe te opstelling een nieuw domein

### Stap 1 - Is dit voor de [!DNL Integration, Staging], of [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] worden niet ondersteund. U moet deze methode gebruiken: [Meerdere websites of winkels instellen: lokale installatie configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikershandleiding.
* **[!DNL Staging]**: Ga naar **Stap 2**.
* **[!DNL Production]**: Ga naar **Stap 3**.

### Stap 2 - [!DNL Staging environment]: ben je aan [!DNL Pro] of [!DNL Starter]?

* **[!DNL Pro]**: **Een aanvraag indienen** om het domein toe te voegen aan [!DNL Fastly, Nginx]en configureert u de [!DNL SSL certificate] en de [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, [de update [!DNL DNS] configuratie met [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>U kunt de nieuwe [!DNL domain] tot [!DNL Fastly] door de configuratie in de [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** zoals in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in onze gebruikershandleiding.

* **[!DNL Starter]**: [!DNL Custom domains] worden niet ondersteund.

### Stap 3 - [!DNL Production environment]: ben je aan [!DNL Pro] of [!DNL Starter]?

* **[!DNL Pro]**: **Een aanvraag indienen** om het domein toe te voegen aan [!DNL Fastly, Nginx]en configureert u de [!DNL SSL certificate] (als de [!DNL Sendgrid domain], indien nodig). Zodra dat is gevormd, blijf **Stap 4**.

>[!NOTE]
>
>U kunt de nieuwe [!DNL domain] tot [!DNL Fastly] door de configuratie in de [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) in onze gebruikershandleiding.

* **[!DNL Starter]**: Voeg de [!DNL domain] aan uw project in **[!DNL Domains]** dan **een verzoek indienen** de **[!DNL ACME Challenge Key]** voor de [!DNL SSL certificate].

### Stap 4 - Is de [!DNL domain] leven?

* **JA**: [Werk de [!DNL DNS] configuratie met [!UICONTROL production] instellingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NEE**: [Werk de [!DNL DNS] configuratie met [!UICONTROL development] instellingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Gerelateerde lezing

* [Meerdere websites of winkels instellen: Nieuwe toevoegen [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) in onze gebruikershandleiding.
