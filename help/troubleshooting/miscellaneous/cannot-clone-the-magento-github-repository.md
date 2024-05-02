---
title: Kan de Magento GitHub-opslagplaats niet klonen
description: Dit artikel verstrekt een moeilijke situatie voor wanneer u niet de bewaarplaats van GitHub van het Magento kunt klonen.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Kan de Magento GitHub-opslagplaats niet klonen

Dit artikel verstrekt een moeilijke situatie voor wanneer u niet de bewaarplaats van GitHub van het Magento kunt klonen.

## Detail {#detail}

Fout is gelijkaardig aan het volgende:

```terminal
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Oplossing {#solution}

Upload uw sleutel van SSH aan GitHub zoals die in wordt besproken [de GitHub Help-pagina](https://help.github.com/articles/generating-ssh-keys) .
