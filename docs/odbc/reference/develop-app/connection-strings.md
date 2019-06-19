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
manager: craigg
ms.openlocfilehash: d7e52ec70e53608f1af48b4abcd2dd1edb4fc454
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042587"
---
# <a name="connection-strings"></a>Строки соединения
Строка подключения содержит сведения, используемые для установления соединения. Полная строка подключения содержит все сведения, необходимые для установления соединения. Строка подключения представляет собой ряд пар "ключевое слово/значение", разделенных точкой с запятой. (Полный синтаксис строки подключения, см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.) Строка подключения используется:  
  
-   **SQLDriverConnect**, который завершает строку подключения, взаимодействие с пользователем.  
  
-   **SQLBrowseConnect**, который завершает строку подключения, который взаимодействует с источником данных.  
  
 **SQLConnect** не использует строку подключения, с помощью **SQLConnect** является аналогом подключение с использованием строки подключения с ровно три пары "ключевое слово/значение" (имя источника данных и, при необходимости пользователь идентификатор и пароль) .
