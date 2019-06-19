---
title: Пример диагностики шлюзов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f4e17074616111ee93ce87c04036d1fc3fd48dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63062422"
---
# <a name="gateways-diagnostic-example"></a>Пример диагностики шлюзов
В архитектуре шлюза драйвер отправляет запросы к шлюзу, поддерживающий ODBC. Шлюз отправляет запросы в СУБД. Так как он является компонентом, который взаимодействует с диспетчером драйверов, драйвер форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например если Oracle Rdb шлюза на основе Microsoft Open Data Services и если Rdb не удалось найти таблицу EMPLOYEE, шлюз может вызвать это диагностическое сообщение:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Из-за ошибки в источнике данных, префикс для идентификатор источника данных ([Rdb]) добавить шлюз в диагностическое сообщение. Так как шлюз был компонента, сопряженный с источником данных, она добавляется префиксы для поставщика ([DEC]) и идентификатор ([ODS шлюз]) диагностическое сообщение. Она также добавляется значение SQLSTATE и код ошибки Rdb в начале диагностическое сообщение. Это разрешено его, чтобы сохранить семантику структуры сообщения и по-прежнему предоставить диагностические сведения ODBC для драйвера. Драйвер выполняет синтаксический анализ сведения об ошибке, подключенные к ошибочную инструкцию шлюзом.  
  
 Так как драйвер шлюза компонент, который взаимодействует с диспетчером драйверов, используется предыдущее сообщение диагностики для форматирования и возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
