---
title: "Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 gekend probleem: dotdigital login"
description: In dit artikel wordt een bekende uitgave van Adobe Commerce 2.3.6, 2.4.0-p1 en 2.4.1 beschreven, waarbij u zich niet via het deelvenster Beheer kunt aanmelden bij [dotdigital] (https://dotdigital.com/) wanneer de digitale account is ingeschakeld.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 gekend probleem: digitale aanmelding

In dit artikel wordt een bekende uitgave beschreven van Adobe Commerce 2.3.6, 2.4.0-p1 en 2.4.1, waarbij u zich niet kunt aanmelden bij [dotdigital](https://dotdigital.com/) via het Admin Panel wanneer de digitale dotaccount is ingeschakeld.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.6 (alleen Safari-browser)
* Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.4.0-p1 (alleen Safari-browser)
* Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.4.1 (alleen Safari-browser)

## Probleem

<u>Vereisten</u>:

1. digitale dotaccount bestaat.
1. Er zijn geldige API-referenties voor dotdigital in Adobe Commerce.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **DOTDIGITAL** > **Chatinstellingen** > **Ingeschakeld** is ingesteld op *Ja.*
1. Klikken op **Configureren** in **Chatwidget configureren** of **Chatteams configureren**.

<u>Verwachte resultaten</u>:

De pagina met chatinstellingen moet worden geopend via het deelvenster Beheer.

<u>Werkelijke resultaten</u>:

Aanmelden bij dotdigital is mislukt.

## Oplossing

Oplossing: gebruik voor deze specifieke situatie een andere browser dan Safari.

## Verwante lezing

[Adobe Commerce 2.4.1 Bekend probleem - Vertexadres dat niet met verschillende verzend-/factureringsadressen valideert](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) in onze kennisbasis voor ondersteuning.
