---
title: "Пример диагностики шлюзов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b14ef1e84b36a0f371f503706fca805c156f2e9d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="gateways-diagnostic-example"></a>Пример диагностики шлюзов
В архитектуре шлюза драйвер отправляет запросы на шлюз, поддерживающий ODBC. Шлюз отправляет запросы СУБД. Поскольку это компонент, который взаимодействует с диспетчером драйверов, драйвер форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например если Oracle шлюза к Rdb на основе Microsoft Open Data Services и если Rdb не удалось найти таблицу СОТРУДНИКОВ, шлюз может создать это диагностическое сообщение:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Из-за ошибки в источнике данных, шлюз добавить диагностическое сообщение префикс для идентификатор источника данных ([Rdb]). Так как шлюз компонента, сопряженный с источником данных, он добавляется префиксы для поставщика ([DEC]) и идентификатор ([ODS шлюз]) диагностическое сообщение. Она также добавляется значение SQLSTATE и код ошибки Rdb начало диагностическое сообщение. Это разрешено его, чтобы сохранить семантику структуры сообщений и по-прежнему указать сведения диагностики ODBC для драйвера. Драйвер анализирует вложенные инструкции ошибка, шлюз сведения об ошибке.  
  
 Поскольку драйвер шлюза компонент, который взаимодействует с диспетчером драйверов, применяется приведенное выше сообщение диагностики для форматирования и возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
