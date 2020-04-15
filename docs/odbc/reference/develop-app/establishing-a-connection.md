---
title: Создание соединения (ru) Документы Майкрософт
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
ms.openlocfilehash: 6f71190a8a2ca1dd8af0d28adb5531540fb1b57e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298704"
---
# <a name="establishing-a-connection"></a>Установление подключения
После выделения обитель и ручки соединения и установки атрибутов соединения приложение готово к подключению к источнику данных или драйверу. Для этого можно использовать три различные функции, которые приложение может использовать: **S'LConnect** (уровень соответствия базовому интерфейсу), **S'LDriverConnect** (Core) и **S'LBrowseConnect** (уровень 1). Каждый из трех предназначен для использования в другом сценарии. Перед подключением приложение может определить, какая из этих функций поддерживается с помощью ключевого слова **ConnectFunctions,** возвращенного **S'LDrivers.**  
  
> [!NOTE]  
>  Некоторые драйверы ограничивают количество активных подключений, которые они поддерживают. Приложение вызывает **S'LGetInfo** с SQL_MAX_DRIVER_CONNECTIONS опцией, чтобы определить, сколько активных соединений поддерживает конкретный драйвер.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Источник данных по умолчанию](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Подключение с помощью SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Строки подключения](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Подключение с помощью SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Подключение с помощью SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
