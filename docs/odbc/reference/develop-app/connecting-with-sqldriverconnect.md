---
title: Подключение с помощью SQLDriverConnect | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78cdaabe867ae67e3a1dfcb80e82cfaf95a94ed1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042220"
---
# <a name="connecting-with-sqldriverconnect"></a>Подключение с помощью SQLDriverConnect
**SQLDriverConnect** используется для подключения к источнику данных, используя строку подключения. **SQLDriverConnect** используется вместо **SQLConnect** по следующим причинам:  
  
-   Чтобы предоставить приложению использовать сведения о соединении специфические для драйвера.  
  
-   для запроса, который драйвер направляет пользователю для получения информации о соединении;  
  
-   Для подключения без указания источника данных.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сведения о подключении для конкретного драйвера](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Запрос сведений о подключении у пользователя](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Подключение с использованием файловых источников данных](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Прямое подключение к драйверам](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
