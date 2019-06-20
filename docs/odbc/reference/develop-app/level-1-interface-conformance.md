---
title: Соответствие интерфейса уровня 1 | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d75c374a7d9d57483dd56e34b51fcb6d89e1b52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213489"
---
# <a name="level-1-interface-conformance"></a>Соответствие интерфейса уровня 1
Уровень соответствия интерфейса уровня 1 включает функциональность на уровне совместимости Core интерфейс, а также дополнительные функции, такие как транзакции, которые обычно доступны в реляционной СУБД с OLTP. Драйвер интерфейса совместимого уровня 1 позволяет приложению выполнить следующий код, наряду с возможностями в уровень соответствия интерфейс Core:  
  
|||  
|-|-|  
|101|Укажите схему базы данных, таблиц и представлений, (с помощью состоящие их двух частей). (Дополнительные сведения см. в разделе трехкомпонентные имена компонентов 201 в [соответствие интерфейса уровня 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Вызовите true асинхронное выполнение функции ODBC, где применимо функции ODBC — синхронными, либо только асинхронные в отдельном соединении.|  
|103|Используйте Прокручиваемые курсоры и тем самым обеспечить доступ к результирующий набор в методах отличный однонаправленные, путем вызова **SQLFetchScroll** с *FetchOrientation* аргументов, отличных от SQL_FETCH_NEXT. (Инструкция SQL_FETCH_BOOKMARK *FetchOrientation* является функция 204 в [соответствие интерфейса уровня 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Получить первичные ключи таблиц, с помощью функции **SQLPrimaryKeys**.|  
|105|Использовать хранимые процедуры, через escape-последовательность ODBC для вызовов процедур и запросы словарь данных о хранимых процедурах, путем вызова **SQLProcedureColumns** и **SQLProcedures**. (Процесс, по которому создаются и хранятся в источнике данных процедуры выходит за рамки данного документа.)|  
|106|Подключение к источнику данных путем интерактивного просмотра доступных серверов, путем вызова **SQLBrowseConnect**.|  
|107|Использование функций ODBC вместо инструкций SQL для выполнения определенных операций базы данных: **SQLSetPos** с SQL_POSITION и SQL_REFRESH.|  
|108|Получить доступ к содержимому несколько результирующих наборов, создаваемые пакеты и хранимые процедуры путем вызова **SQLMoreResults**.|  
|109|Разделение транзакциях, объединяющих несколько функций ODBC, с true атомарность и возможность указывать SQL_ROLLBACK в **SQLEndTran**.|
