---
title: Уровень 2 Интерфейс Соответствие (ru) Документы Майкрософт
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
ms.openlocfilehash: 3ee57d716cbb93f855e1fd78d41bff62a681eb6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306166"
---
# <a name="level-2-interface-conformance"></a>Соответствие интерфейса уровня 2
Уровень 2 уровня соответствия интерфейса включает в себя уровень 1 интерфейс соответствия уровня функциональности плюс следующие функции:  
  
|||  
|-|-|  
|201|Используйте три части таблиц и представлений баз данных. (Для получения дополнительной информации см. функцию поддержки именования в двух частей 101 [в соответствии интерфейса уровня 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Опишите динамические параметры, позвонив по **телефону S'LDescribeParam**.|  
|203|Используйте не только входные параметры, но и параметры вывода и ввода/вывода, а также значения результатов сохраненных процедур.|  
|204|Используйте закладки, в том числе получение закладок, позвонив по **телефону S'LDescribeCol** и **S'LColAttribute** на столбце номер 0; извлечение на основе закладки, позвонив **в S'LFetchScroll** с аргументом *FetchOrientation,* установленным для SQL_FETCH_BOOKMARK; и обновлять, удалять и получать операции закладок, вызывая **S'LBulkOperations** с аргументом *операции,* установленным для SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK или SQL_FETCH_BY_BOOKMARK.|  
|205|Извлекай расширенную информацию о словаре данных, позвонив по **s'LColumnPrivileges,** **S'LForeignKeys**и **S'LTablePrivileges.**|  
|206|Для выполнения дополнительных операций с базой данных используйте функции ODBC вместо инструкций по СЗЛ, вызывая **s'LBulkOperations** с SQL_ADD или **S'LSetPos** с SQL_DELETE или SQL_UPDATE. (Поддержка вызовов на **S'LSetPos** с аргументом *LockType,* установленным для SQL_LOCK_EXCLUSIVE или SQL_LOCK_UNLOCK, не является частью уровней соответствия, но является дополнительной функцией.)|  
|207|Включить асинхронное выполнение функций ODBC для определенных отдельных инструкций.|  
|208|Получить SQL_ROWVER столбец строки таблиц, позвонив по **S'LSpecialColumns**. (Для получения дополнительной информации, см. поддержку **для S'LSpecialColumns** с *аргументом IdentifierType,* установленным для SQL_BEST_ROWID как функция 20 в [core Interface Conformance.)](../../../odbc/reference/develop-app/core-interface-conformance.md)|  
|209|Установите атрибут SQL_ATTR_CONCURRENCY оператора по крайней мере одним значением, кроме SQL_CONCUR_READ_ONLY.|  
|210|Возможность тайм-аута запроса входа и запросов s-L (SQL_ATTR_LOGIN_TIMEOUT и SQL_ATTR_QUERY_TIMEOUT).|  
|211|Возможность изменения уровня изоляции по умолчанию; возможность выполнять транзакции с "серийным" уровнем изоляции.|
