---
title: Сравнение закладок Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307479"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Поскольку закладки сопоставимы с байт-равными, их можно сравнить с равенством или неравенством. Для этого приложение рассматривает каждую закладку как массив байтов и сравнивает две закладки байт-байт. Поскольку закладки гарантированно отличаются только в наборе результатов, нет смысла сравнивать закладки, полученные из различных наборов результатов.
