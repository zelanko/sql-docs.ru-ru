---
title: Пример диагностики на основе СУБД драйвера | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e688fff2771a14d85a659ae7c69d6a515ce88f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
