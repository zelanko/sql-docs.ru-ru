---
title: "Пример диагностики на основе СУБД драйвера | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c0a20af8dc2a35ba451890472ad1af73e01d8688
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="dbms-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе DBMS
Драйвер на основе СУБД отправляет запросы к СУБД и возвращает сведения в приложение через диспетчер драйверов. Поскольку драйвер — это компонент, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если с помощью SQL-служб, драйвер Microsoft для Oracle Rdb обнаружил недопустимое имя курсора может возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Из-за ошибки в драйвере, он добавляется префиксы диагностическое сообщение для поставщика ([Microsoft]) и драйвер ([Rdb драйвер ODBC]).  
  
 СУБД не удалось найти таблицу СОТРУДНИКОВ, драйвер может форматировать и возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Из-за ошибки в источнике данных, драйвер добавлен префикс для идентификатор источника данных ([Rdb]) диагностическое сообщение. Так как драйвер компонента, сопряженный с источником данных, он добавляется префиксы для поставщика ([Microsoft]) и идентификатор ([Rdb драйвер ODBC]) диагностическое сообщение.

