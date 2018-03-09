---
title: "Соединение с помощью SQLDriverConnect | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9f6177b384da8866c8140cc30f1d32bca0bb635
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-with-sqldriverconnect"></a>Соединение с помощью SQLDriverConnect
**SQLDriverConnect** используется для подключения к источнику данных с помощью строки подключения. **SQLDriverConnect** используется вместо **SQLConnect** по следующим причинам:  
  
-   Передать приложению использовать сведения о соединении с драйвером.  
  
-   для запроса, который драйвер направляет пользователю для получения информации о соединении;  
  
-   Для соединения без указания источника данных.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сведения о подключении для конкретного драйвера](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Запрос сведений о подключении у пользователя](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Подключение с использованием файловых источников данных](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Прямое подключение к драйверам](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
