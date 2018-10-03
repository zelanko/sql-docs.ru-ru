---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f3828129c2a0ed4183bbefce8daf68cee1d95f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668302"
---
# <a name="level-2-interface-conformance"></a>Соответствие интерфейса уровня 2
Уровень соответствия интерфейса уровня 2 включает функциональные возможности уровня 1 уровень соответствия — интерфейс, а также следующие возможности:  
  
|||  
|-|-|  
|201|Используйте трехкомпонентные имена таблиц базы данных и представлений. (Дополнительные сведения см. в разделе двухкомпонентное именования средство поддержки 101 [соответствие интерфейса уровня 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Описания динамических параметров, вызвав **SQLDescribeParam**.|  
|203|Используйте не только входные параметры, но также выходные и входные и выходные параметры и значения результатов хранимых процедур.|  
|204|Использование закладок, включая извлечение закладок, путем вызова **SQLDescribeCol** и **SQLColAttribute** разбивается по столбцу номер 0; получение основанный на закладке, путем вызова **SQLFetchScroll** с *FetchOrientation* значением sql_fetch_bookmark аргумента; и обновление, удаление и получить операциями закладки, вызвав **SQLBulkOperations** с *Операции* аргумент значение SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK.|  
|205|Получить дополнительные сведения о данных словаря, путем вызова **SQLColumnPrivileges**, **SQLForeignKeys**, и **SQLTablePrivileges**.|  
|206|Использование функции ODBC вместо инструкций SQL для выполнения операций дополнительную базу данных, вызвав **SQLBulkOperations** с SQL_ADD, или **SQLSetPos** с SQL_DELETE или SQL_UPDATE. (Поддержка вызовов **SQLSetPos** с *LockType* SQL_LOCK_EXCLUSIVE или SQL_LOCK_UNLOCK аргумент не является частью уровни соответствия, но является дополнительным компонентом.)|  
|207|Включите асинхронное выполнение функций ODBC для указанного отдельных инструкций.|  
|208|Получить, вызвав таблиц, столбец идентификации строки SQL_ROWVER **SQLSpecialColumns**. (Дополнительные сведения см. в статье поддержка **SQLSpecialColumns** с *IdentifierType* аргумент значение SQL_BEST_ROWID как функцию в 20 [соответствие основного интерфейса](../../../odbc/reference/develop-app/core-interface-conformance.md) .)|  
|209|Значение атрибута инструкции SQL_ATTR_CONCURRENCY по крайней мере одно значение, отличное от SQL_CONCUR_READ_ONLY.|  
|210|Возможность времени ожидания запроса на вход и запросов SQL (SQL_ATTR_LOGIN_TIMEOUT и SQL_ATTR_QUERY_TIMEOUT).|  
|211|Возможность изменить уровень изоляции по умолчанию; возможность выполнения транзакций с уровнем изоляции «сериализуемые».|
