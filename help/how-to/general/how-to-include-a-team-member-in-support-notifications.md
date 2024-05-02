---
title: Hoe te om een teamlid in de berichten van de Steun te omvatten
description: In dit artikel wordt uitgelegd hoe u een teamlid kunt opnemen in ondersteuningsmeldingen.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Hoe te om een teamlid in de berichten van de Steun te omvatten

In dit artikel wordt uitgelegd hoe u een teamlid opneemt om automatisch updates van de ondersteuning via e-mailmeldingen te ontvangen.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Oorzaak

* Het teamlid is niet toegevoegd aan de [!DNL cloud project] met de nodige bevoegdheden.
* Het teamlid heeft geen ondersteuningsaccount.

## Oplossing

1. Ga naar de **[!DNL Cloud Project URL]** (Voorbeeld: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Verifieer of het teamlid aan het project is toegevoegd en een [!DNL Super User].

Als ze niet nodig zijn [!DNL cloud project] toegang, een [Ondersteuningsverzoek in het Adobe Commerce-ondersteuningscentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) aan automatisch CC: zij op alle kaartjes en ook verstrekken hun **[!DNL MAGE ID]** (indien beschikbaar).

Als zij niet aan het project zijn toegevoegd, zult u hen als a moeten toevoegen [!DNL Super User] en subsidie [!DNL Shared Access]:

* [Gebruikerstoegang beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in onze gebruikershandleiding.
* [Kan gebruiker niet toevoegen aan Adobe Commerce Cloud Project](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) in onze Commerce Knowledge Base.
* [Adobe Commerce Help Center Handboek: Gedeelde toegang](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) in onze Commerce Knowledge Base.

Indien deze aan de [!DNL cloud project], maar niet over de [!DNL Super User role], hun [!DNL role] dienovereenkomstig in [Gebruikerstoegang beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Gerelateerde lezing

[Oude teamleden ontvangen e-mailberichten over de cloud van Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
