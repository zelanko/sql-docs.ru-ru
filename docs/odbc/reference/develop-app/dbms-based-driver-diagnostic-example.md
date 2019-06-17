---
title: Пример диагностики драйверов на основе СУБД | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0485ecf720cb84580c17c77b31fc6816de2e679a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641037"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе СУБД
Драйверов на основе СУБД отправляет запросы к СУБД и возвращает сведения в приложение через диспетчер драйверов. Так как драйвер является компонентом, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если используется SQL и служб, драйвер Майкрософт для Oracle Rdb обнаружил недопустимое имя курсора, могут возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Из-за ошибки в драйвере, она добавляется префиксы диагностическое сообщение для поставщика ([Microsoft]) и драйвер ([драйвер ODBC для Rdb]).  
  
 Если СУБД не удалось найти таблицу СОТРУДНИКОВ, драйвер может форматировать и вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Из-за ошибки в источнике данных, драйвер добавлен префикс для идентификатор источника данных ([Rdb]) для диагностическое сообщение. Так как драйвер не компонент, сопряженный с источником данных, она добавляется префиксы для поставщика ([Microsoft]) и идентификатор ([драйвер ODBC для Rdb]) диагностическое сообщение.
