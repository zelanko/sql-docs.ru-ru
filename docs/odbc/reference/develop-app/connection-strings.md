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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036421"
---
# <a name="connection-strings"></a>Строки подключения
Строка подключения содержит сведения, используемые для установления соединения. Полная строка подключения содержит все сведения, необходимые для установления соединения. Строка подключения представляет собой ряд пар "ключевое слово/значение", разделенных точкой с запятой. (Полный синтаксис строки подключения, см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.) Строка подключения используется:  
  
-   **SQLDriverConnect**, который завершает строку подключения, взаимодействие с пользователем.  
  
-   **SQLBrowseConnect**, который завершает строку подключения, который взаимодействует с источником данных.  
  
 **SQLConnect** не использует строку подключения, с помощью **SQLConnect** является аналогом подключение с использованием строки подключения с ровно три пары "ключевое слово/значение" (имя источника данных и, при необходимости пользователь идентификатор и пароль) .
