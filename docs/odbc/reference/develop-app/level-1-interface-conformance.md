---
title: Соответствие интерфейс уровня 1 | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: faae1bf56dd28f83fa3fec5c340bcf67c302def3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="level-1-interface-conformance"></a>Соответствие интерфейс уровня 1
Уровень соответствия уровня 1 интерфейс включает функциональные возможности уровня соответствия основной интерфейс, а также дополнительные компоненты, например транзакции, которые обычно осуществляется в реляционных СУБД с OLTP. Драйвер уровня 1 интерфейс совместимую позволяет приложению выполните следующие действия, в дополнение к возможности уровень соответствия основной интерфейс:  
  
|||  
|-|-|  
|101|Укажите схему базы данных, таблиц и представлений (с помощью состоящие из двух частей). (Дополнительные сведения см. в разделе трехкомпонентные компонентов 201 в [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Вызов функции ODBC, где применимо функции ODBC — всего синхронного или все асинхронные в отдельном соединении true асинхронное выполнение.|  
|103|Использование Прокручиваемые курсоры и тем самым доступ в результирующем наборе в методах, отличного от однонаправленные, путем вызова **SQLFetchScroll** с *FetchOrientation* аргумент, отличный от SQL_FETCH_NEXT. (SQL_FETCH_BOOKMARK *FetchOrientation* в компонент 204 [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Первичные ключи таблиц, получить, вызвав **SQLPrimaryKeys**.|  
|105|Использование хранимых процедур через escape-последовательность ODBC для вызовов процедур и запросов словарь данных относительно хранимые процедуры путем вызова **SQLProcedureColumns** и **SQLProcedures**. (Процесс, с помощью которого создаются и хранятся в источнике данных процедуры выходит за рамки данного документа.)|  
|106|Соединиться с источником данных путем интерактивного просмотра доступных серверов путем вызова **SQLBrowseConnect**.|  
|107|Использование функции ODBC вместо инструкций SQL для выполнения определенных операций базы данных: **SQLSetPos** с SQL_POSITION и SQL_REFRESH.|  
|108|Получить доступ к содержимому несколько результирующих наборов, создаваемые пакеты и хранимые процедуры путем вызова **SQLMoreResults**.|  
|109|Разделения транзакциях, объединяющих несколько функций ODBC с true атомарность и возможность указывать SQL_ROLLBACK в **SQLEndTran**.|
