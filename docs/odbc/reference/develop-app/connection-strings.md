---
title: Строки подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbbb5b4672a8ea393380063887cfd77b3e910238
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299034"
---
# <a name="connection-strings"></a>Строки соединения
Строка подключения содержит сведения, используемые для установления соединения. Полная строка подключения содержит все сведения, необходимые для установления соединения. Строка подключения представляет собой ряд пар "ключевое слово-значение", разделенных точкой с запятой. (Полный синтаксис строки подключения см. в описании функции [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) .) Строка подключения используется:  
  
-   **SQLDriverConnect**, который завершает строку подключения путем взаимодействия с пользователем.  
  
-   **SQLBrowseConnect**, который последовательно завершает строку подключения с источником данных.  
  
 **SQLConnect** не использует строку подключения; использование **SQLConnect** аналогично соединению с использованием строки подключения, состоящих из трех пар "ключевое слово-значение" (для имени источника данных и, при необходимости, идентификатора пользователя и пароля).
