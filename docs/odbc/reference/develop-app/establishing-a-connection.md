---
description: Установление подключения
title: Установление соединения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establishing a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establishing a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4256f3f0fe3e082b789d3758ece9bf7c8919eacb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482937"
---
# <a name="establishing-a-connection"></a>Установление подключения
После выделения среды и дескрипторов соединений и установки атрибутов соединения приложение будет готово к подключению к источнику данных или драйверу. Существует три различные функции, которые приложение может использовать для этого: **SQLConnect** (уровень соответствия основных интерфейсов), **SQLDriverConnect** (Core) и **SQLBrowseConnect** (уровень 1). Каждое из трех предназначено для использования в другом сценарии. Перед подключением приложение может определить, какие из этих функций поддерживаются с помощью ключевого слова **коннектфунктионс** , возвращаемого **SQLDrivers**.  
  
> [!NOTE]  
>  Некоторые драйверы ограничивают количество активных подключений, которые они поддерживают. Приложение вызывает **SQLGetInfo** с параметром SQL_MAX_DRIVER_CONNECTIONS, чтобы определить, сколько активных подключений поддерживает конкретный драйвер.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Источник данных по умолчанию](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Подключение с помощью SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Строки подключения](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Подключение с помощью SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Подключение с помощью SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
