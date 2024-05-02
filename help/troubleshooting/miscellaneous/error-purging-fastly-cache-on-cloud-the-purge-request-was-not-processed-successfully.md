---
title: Fout bij snel leegmaken van cache op Cloud (de aanvraag voor leegmaken is niet verwerkt)
description: 'Dit artikel bevat een oplossing voor het gebruik van een optie voor snel leegmaken en u ontvangt de fout: *De aanvraag voor leegmaken is niet verwerkt*. De snelst is een CDN en het in het voorgeheugen onderbrengen dienst inbegrepen met Adobe Commerce op de plannen en de implementaties van de wolkeninfrastructuur. Als u een optie voor snel leegmaken probeert te gebruiken en deze niet wordt verwerkt, hebt u mogelijk onjuiste gegevens in de omgeving of een probleem aangetroffen.'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Fout bij snel leegmaken van cache op Cloud (de aanvraag voor leegmaken is niet verwerkt)

Dit artikel bevat een oplossing voor het gebruik van een optie voor het snel leegmaken en u ontvangt de fout: *Het verwijderingsverzoek is niet verwerkt*. De snelst is een CDN en het in het voorgeheugen onderbrengen dienst inbegrepen met Adobe Commerce op de plannen en de implementaties van de wolkeninfrastructuur. Als u een optie voor het snel leegmaken probeert te gebruiken en deze niet verwerkt, hebt u mogelijk onjuiste gegevens in de omgeving of een probleem aangetroffen.

Met deze informatie kunt u snel headers voor uw livesite en oorspronkelijke servers controleren en testen.

## Betrokken versies

* Adobe Commerce op cloudinfrastructuur 2.1.X en hoger
* Snelst 1.2.27 en hoger

## Probleem

Caching werkt, maar als je probeert te wissen, krijg je een fout of werkt het niet. De fout bevat: &quot;Het verwijderingsverzoek is niet met succes verwerkt.&quot;

## Oorzaak

U hebt mogelijk onjuiste referenties ingesteld in uw omgeving of u moet VCL-fragmenten uploaden.

## Oplossen

### Controleer de gegevens snel

Controleer of u over de juiste snelste service-id en API-token in uw omgeving beschikt. Als u het Staging geloofsbrieven in Productie hebt, kunnen de zuiveringen niet verkeerd verwerken of verwerken.

1. Meld u als beheerder aan bij uw lokale Commerce-beheerder.
1. Klikken **Winkels** > Instellingen > **Configuratie** > **Geavanceerd** > **Systeem** en uitbreiden **Volledige paginacache**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Vouw de configuratie snel uit en controleer de snelste service-id en API-token voor uw omgeving.
1. Als u de waarden wijzigt, klikt u op Referenties testen.

### VCL-fragmenten controleren

Als de geloofsbrieven correct zijn, kunt u problemen met uw VCLs hebben. Om van uw VCL per dienst een lijst te maken en te herzien, ga de volgende API vraag in een terminal in:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Controleer de lijst met VCL&#39;s. Als u problemen hebt met de standaard-VCL&#39;s van Snelst, kunt u de inhoud opnieuw uploaden of verifiëren volgens de [Snelle standaard VCL&#39;s](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Ga voor het bewerken van uw aangepaste VCL&#39;s naar [Aangepaste, snel VCL-fragmenten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) in de Commerce on Cloud Infrastructure Guide.

## Meer informatie

In onze documentatie voor ontwikkelaars:

* [Info snel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Snel instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Aangepaste, snel VCL-fragmenten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
