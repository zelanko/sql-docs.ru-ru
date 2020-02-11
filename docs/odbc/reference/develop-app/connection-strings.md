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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f68a87db729df2f4a27e2766a9de60e8c75a71a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036421"
---
# <a name="connection-strings"></a>Строки соединения
Строка подключения содержит сведения, используемые для установления соединения. Полная строка подключения содержит все сведения, необходимые для установления соединения. Строка подключения представляет собой ряд пар "ключевое слово-значение", разделенных точкой с запятой. (Полный синтаксис строки подключения см. в описании функции [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) .) Строка подключения используется:  
  
-   **SQLDriverConnect**, который завершает строку подключения путем взаимодействия с пользователем.  
  
-   **SQLBrowseConnect**, который последовательно завершает строку подключения с источником данных.  
  
 **SQLConnect** не использует строку подключения; использование **SQLConnect** аналогично соединению с использованием строки подключения, состоящих из трех пар "ключевое слово-значение" (для имени источника данных и, при необходимости, идентификатора пользователя и пароля).
