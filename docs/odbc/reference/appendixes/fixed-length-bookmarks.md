---
description: Закладки фиксированной длины
title: Закладки с фиксированной длиной | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d357ba96141c658889628941c7f9492db5fd6b66
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466180"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если драйвер ODBC *3. x* должен работать с приложением ODBC *2. x* , использующим закладки фиксированной длины, драйвер должен поддерживать следующее:  
  
-   SQL_UB_ON в качестве значения параметра инструкции SQL_USE_BOOKMARKS. (SQL_UB_ON не рекомендуется использовать в ODBC *3. x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
