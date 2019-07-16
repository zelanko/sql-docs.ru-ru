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
ms.openlocfilehash: ef42fe2ab881a7e24d680e0dd941cbea0d95488f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076896"
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
