---
title: Подключения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70f459f60616e7edd77078a7e9653ab9dff097e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248345"
---
# <a name="establishing-a-connection"></a>Установление подключения
После выделения среды и дескрипторов соединения и установки любых атрибутов соединения, приложение сможет подключиться к источнику данных или драйверу. Существует три разных функций, которые приложение может использовать для этого: **SQLConnect** (Core уровень соответствия интерфейса), **SQLDriverConnect** (ядро), и **SQLBrowseConnect** (уровень 1). Каждая из трех предназначен для использования в другом сценарии. Перед подключением, приложение может определить, какие из этих функций поддерживается с **ConnectFunctions** ключевое слово, возвращенный **SQLDrivers**.  
  
> [!NOTE]  
>  Некоторые драйверы Ограничьте число активных подключений, которые они поддерживают. Приложение вызывает **SQLGetInfo** SQL_MAX_DRIVER_CONNECTIONS возможность определить, сколько активных подключений поддерживает драйвер.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Источник данных по умолчанию](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Подключение с помощью SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Строки подключения](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Подключение с помощью SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Подключение с помощью SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
