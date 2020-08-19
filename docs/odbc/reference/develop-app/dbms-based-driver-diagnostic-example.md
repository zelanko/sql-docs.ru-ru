---
description: Пример диагностики драйверов на основе СУБД
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
ms.openlocfilehash: 5425afb18a5582a840966798ea7a7209dba7e1e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424746"
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
