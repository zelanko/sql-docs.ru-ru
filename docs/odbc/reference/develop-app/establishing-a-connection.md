---
title: Подключения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establising a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establising a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d433869c3ae7cff9921210c25fce6757f36180b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910707"
---
# <a name="establishing-a-connection"></a>Подключения
После выделения памяти для среды и дескрипторов соединения, а также установки любых атрибутов соединения, приложение сможет подключиться к источнику данных или драйверу. Есть три различные функции, приложение может использовать для этого: **SQLConnect** (основной интерфейс уровень соответствия), **SQLDriverConnect** (Core) и **SQLBrowseConnect**(Уровень 1). Каждая из трех предназначен для использования в другом сценарии. Перед подключением, приложение может определить, какой из этих функций поддерживается с **ConnectFunctions** ключевое слово, возвращенных **SQLDrivers**.  
  
> [!NOTE]  
>  Некоторые драйверы ограничить число активных подключений, которые они поддерживают. Приложение вызывает **SQLGetInfo** SQL_MAX_DRIVER_CONNECTIONS возможность определить, сколько активных подключений поддерживает конкретного драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Источник данных по умолчанию](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Подключение с помощью SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Строки подключения](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Подключение с помощью SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Подключение с помощью SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
