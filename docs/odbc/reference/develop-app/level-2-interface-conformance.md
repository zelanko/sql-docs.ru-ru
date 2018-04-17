---
title: Соответствие интерфейс уровня 2 | Документы Microsoft
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
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a97e36132b3dc386106f1c48cdb6f2147cf9610
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="level-2-interface-conformance"></a>Соответствие интерфейс уровня 2
Уровень соответствия интерфейс уровня 2 включает функциональные возможности уровня 1 интерфейс — уровень соответствия, плюс следующие возможности:  
  
|||  
|-|-|  
|201|Используйте трехкомпонентные имена таблиц базы данных и представлений. (Дополнительные сведения см. в разделе двух частей именования средство поддержки 101 [согласованности интерфейс на уровне 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Описания динамических параметров, вызвав **SQLDescribeParam**.|  
|203|Используйте не только входные параметры, но также выходных и входных/выходных параметров и результирующих значений, хранимых процедур.|  
|204|Использование закладок, включая получение закладки, путем вызова **SQLDescribeCol** и **SQLColAttribute** на столбец номер 0; Выборка основан на закладку, путем вызова **SQLFetchScroll** с *FetchOrientation* значением SQL_FETCH_BOOKMARK; и обновления, удаления и выберите закладку операции, путем вызова метода **SQLBulkOperations** с *Операции* аргументу присвоено SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK.|  
|205|Получить дополнительные сведения о словаря данных путем вызова **SQLColumnPrivileges**, **SQLForeignKeys**, и **SQLTablePrivileges**.|  
|206|Использование функции ODBC вместо инструкции SQL для выполнения операций дополнительную базу данных, вызвав **SQLBulkOperations** с SQL_ADD, или **SQLSetPos** с SQL_DELETE или SQL_UPDATE. (Поддержка вызовы **SQLSetPos** с *LockType* SQL_LOCK_EXCLUSIVE или SQL_LOCK_UNLOCK аргумент не является частью уровни согласованности, но является дополнительным компонентом.)|  
|207|Включите асинхронное выполнение функции ODBC для указанного отдельных инструкций.|  
|208|Получить SQL_ROWVER столбец идентификации строк таблиц, путем вызова **SQLSpecialColumns**. (Дополнительные сведения см. в разделе поддержка **SQLSpecialColumns** с *IdentifierType* аргументу присвоено SQL_BEST_ROWID как компонент в 20 [соответствия основной интерфейс](../../../odbc/reference/develop-app/core-interface-conformance.md) .)|  
|209|Значение атрибута инструкции SQL_ATTR_CONCURRENCY по крайней мере одно значение, отличное от SQL_CONCUR_READ_ONLY.|  
|210|Возможность запрос времени ожидания входа в систему и запросов SQL (параметре и SQL_ATTR_QUERY_TIMEOUT).|  
|211|Возможность изменить уровень изоляции по умолчанию; возможность выполнения транзакций с уровнем изоляции «serializable».|
