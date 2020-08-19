---
description: Сравнение закладок
title: Сравнение закладок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 939c3780fc9c6738a307e9a969a346951cfac5e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476786"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Поскольку закладки являются сравнимыми по байтам, их можно сравнивать на равенство или неравенство. Для этого приложение обрабатывает каждую закладку как массив байтов и сравнивает две закладки в байтах по байтам. Так как закладки гарантированно отличаются только в результирующем наборе, нет смысла сравнивать закладки, полученные из разных результирующих наборов.
