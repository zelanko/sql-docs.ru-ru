---
title: Строки подключения Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299034"
---
# <a name="connection-strings"></a>Строки подключения
Строка соединения содержит информацию, используемую для установления соединения. Полная строка соединения содержит всю информацию, необходимую для установления соединения. Строка соединения представляет собой серию пар ключевых слов/значений, разделенных запятыми. (Для полного синтаксиса строки [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) соединения см. Строка соединения используется:  
  
-   **S'LDriverConnect**, который завершает строку соединения путем взаимодействия с пользователем.  
  
-   **S'LBrowseConnect**, который завершает строку соединения итеративно с источником данных.  
  
 **S'LConnect** не использует строку соединения; использование **S'LConnect** аналогично подключению с помощью строки соединения с ровно тремя парами ключевых слов/значения (для имени источника данных и, по желанию, идентификатора пользователя и пароля).
