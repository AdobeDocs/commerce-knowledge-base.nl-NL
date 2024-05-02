---
title: Kan geen toegang krijgen tot juiste Adobe Commerce-account/-project of het project ontbreekt in uw account
description: Dit artikel bevat een oplossing voor het probleem wanneer u geen toegang hebt tot het correcte Adobe Commerce-project voor de cloud wanneer er eigendomswijzigingen of wijzigingen in e-mailadressen zijn.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Kan geen toegang krijgen tot de juiste cloudaccount/het juiste project of het project ontbreekt in uw account

Dit artikel bevat een oplossing voor de volgende problemen nadat de accounteigenaar of het bijbehorende e-mailadres is gewijzigd:

1. U hebt geen toegang tot de juiste Adobe Commerce-projecten voor de cloud.
1. Er worden geen cloud Adobe Commerce-projecten onder uw account weergegeven op [accounts.magento.cloud/user](https://accounts.magento.cloud/user).
1. U ziet de gegevens van een andere account (de vorige rekeninghouder) op [accounts.magento.cloud/user](https://accounts.magento.cloud/user).

## Probleem

U hebt geen toegang tot het correcte Adobe Commerce-project voor de cloud als er wijzigingen zijn in eigenaren of in e-mailadressen.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Oorzaak

Deze kwestie gebeurt typisch wanneer enig teken-op (SSO) van de vorige projecteigenaar nog met Adobe.com na is geïntegreerd:

1. De eigendom van het wolkenproject is overgedragen aan u (de gebruiker) en u ziet de oorspronkelijke account van de eigenaar van het project. Klik hier voor de [oplossing](#solution-for-cause-one-and-two).

   OF

1. U (de gebruiker) hebt naar een ander bedrijf verhuisd, samen met een wijziging in het e-mailadres en de projecten waartoe u toegang hebt. U ziet de projecten u toegang tot in uw vorige rol/bedrijf werd verleend. Klik hier voor de [oplossing](#solution-for-cause-one-and-two).

   OF

1. U hebt uw e-mailadres op https://account.adobe.com gewijzigd in een ander e-mailadres dat momenteel niet aan een wolkenproject is gekoppeld. Klik hier voor de [oplossing](#solution-for-cause-three).

## Oplossing voor één of twee {#solution-for-cause-one-and-two}

De oplossing voor wanneer de kwestie door één en twee wordt veroorzaakt is het losmaken van de enige sign-on integratie met Adobe.com. Voer de onderstaande stappen uit om de verbinding te verbreken:

1. Vouw vanuit https://accounts.magento.cloud/user de **[!UICONTROL Single Sign-On]** sectie. Klikken **[!UICONTROL Disconnect from Adobe.com]** te verbreken.

   ![single-sign-on-adobe-connect](assets/sso-adobe-disconnect.png)

1. Klik op **[!UICONTROL Disconnect]**.

   ![adobe-disconnect](assets/adobe-disconnect.png)

1. Afmelden.
1. Klik op de knop **[!UICONTROL Adobe.com]** knop.

   ![Magento.com](assets/adobe-welcome-login.png)

1. U moet nu het juiste account kunnen zien en toegang krijgen tot het juiste cloudproject.

## Oplossing voor drie {#solution-for-cause-three}

Als de kwestie door oorzaak drie is veroorzaakt, vraag een bestaande supergebruiker op het project om uw nieuw e-mailadres aan het project toe te voegen. Raadpleeg voor meer informatie [Gebruikerstoegang beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
