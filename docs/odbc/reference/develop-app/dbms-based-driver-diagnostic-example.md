---
title: Пример диагностики драйвера на основе СУБД | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304355"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе СУБД
Драйвер на основе СУБД отправляет запросы СУБД и возвращает сведения в приложение с помощью диспетчера драйверов. Поскольку драйвер является компонентом, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если при использовании SQL/Services драйвер Microsoft для Oracle RDB обнаружил недопустимое имя курсора, он может вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Поскольку ошибка произошла в драйвере, она добавила префиксы в диагностическое сообщение для поставщика ([Microsoft]) и драйвера ([драйвер ODBC RDB]).  
  
 Если СУБД не удалось найти таблицу EMPLOYEE, драйвер может отформатировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Так как в источнике данных произошла ошибка, драйвер добавил префикс для идентификатора источника данных ([RDB]) в диагностическое сообщение. Поскольку драйвер был компонентом, который взаимосвязан с источником данных, он добавил префиксы для своего поставщика ([Microsoft]) и идентификатор ([драйвер ODBC RDB]) в диагностическое сообщение.
