---
title: DBMS-диагностика драйвера Пример (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f43548d2b57233dea6f7423e6bad67b6233b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304355"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе СУБД
Драйвер на основе DBMS отправляет запросы в DBMS и возвращает информацию в приложение через менеджера драйвера. Поскольку драйвер является компонентом, который взаимодействует с менеджером драйвера, он форматирует и возвращает аргументы для **S'LGetDiagRec.**  
  
 Например, если, используя S'L/Services, драйвер Корпорации Майкрософт для Oracle Rdb столкнулся с недействительным именем курсора, он может вернуть следующие значения из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Поскольку ошибка произошла в драйвере, он добавил префиксы к диагностическому сообщению для поставщика («Microsoft») и драйвера («ODBC Rdb Driver»).  
  
 Если DBMS не смог найти таблицу EMPLOYEE, драйвер может отформатировать и вернуть следующие значения из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Поскольку ошибка произошла в источнике данных, драйвер добавил префикс для идентификатора источника данных (Rdb) в диагностическое сообщение. Поскольку драйвер был компонентом, который взаимодействовал с источником данных, он добавил префиксы для своего поставщика («Microsoft») и идентификатор («ODBC Rdb Driver») к диагностическому сообщению.
