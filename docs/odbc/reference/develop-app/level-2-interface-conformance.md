---
description: Соответствие интерфейса уровня 2
title: Соответствие интерфейса уровня 2 | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b7148b05d3870a7f23a51167fffeb1860c26d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476566"
---
# <a name="level-2-interface-conformance"></a>Соответствие интерфейса уровня 2
Уровень соответствия интерфейсов уровня 2 включает в себя функции уровня соответствия интерфейсов уровня 1 и следующие функции:  
  
|Номер функции|Описание|  
|-|-|  
|201|Используйте имена из трех частей в таблицах и представлениях базы данных. (Дополнительные сведения см. в разделе Поддержка именования, состоящие из двух частей, 101 в разделе [соответствие интерфейса уровня 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Опишите динамические параметры, вызвав **SQLDescribeParam**.|  
|203|Используйте не только входные параметры, но и выходные и входные и выходные параметры, а также результирующие значения хранимых процедур.|  
|204|Используйте закладки, включая извлечение закладок, вызвав **SQLDescribeCol** и **SQLColAttribute** в столбце номер 0; получение на основе закладки путем вызова **SQLFetchScroll** с аргументом *фетчориентатион* , для которого задано значение SQL_FETCH_BOOKMARK; и обновления, удаления и выборки с помощью операций с закладками путем вызова **SQLBulkOperations** с аргументом *операции* , для которого задано значение SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK.|  
|205|Получите дополнительные сведения о словаре данных, вызвав **SQLColumnPrivileges**, **SQLForeignKeys**и **SQLTablePrivileges**.|  
|206|Используйте функции ODBC вместо инструкций SQL для выполнения дополнительных операций с базой данных, вызвав **SQLBulkOperations** с SQL_ADD или **SQLSetPos** с SQL_DELETE или SQL_UPDATE. (Поддержка вызовов функции **SQLSetPos** с аргументом *LockType* , равным SQL_LOCK_EXCLUSIVE или SQL_LOCK_UNLOCK, не является частью уровней соответствия, но является дополнительным компонентом.)|  
|207|Включить асинхронное выполнение функций ODBC для указанных отдельных инструкций.|  
|208|Получите SQL_ROWVER столбец, идентифицирующий строки таблиц, вызвав **SQLSpecialColumns**. (Дополнительные сведения см. в описании поддержки **SQLSpecialColumns** с аргументом *идентифиертипе* , для которого задано значение SQL_BEST_ROWID в качестве функции 20 в соответствии с [базовым интерфейсом](../../../odbc/reference/develop-app/core-interface-conformance.md).)|  
|209|Задайте для атрибута инструкции SQL_ATTR_CONCURRENCY хотя бы одно значение, отличное от SQL_CONCUR_READ_ONLY.|  
|210|Возможность истечения времени ожидания запроса на вход и запросов SQL (SQL_ATTR_LOGIN_TIMEOUT и SQL_ATTR_QUERY_TIMEOUT).|  
|211|Возможность изменения уровня изоляции по умолчанию; возможность выполнения транзакций с уровнем изоляции "Serializable".|
