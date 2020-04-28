---
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
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307479"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Поскольку закладки являются сравнимыми по байтам, их можно сравнивать на равенство или неравенство. Для этого приложение обрабатывает каждую закладку как массив байтов и сравнивает две закладки в байтах по байтам. Так как закладки гарантированно отличаются только в результирующем наборе, нет смысла сравнивать закладки, полученные из разных результирующих наборов.
