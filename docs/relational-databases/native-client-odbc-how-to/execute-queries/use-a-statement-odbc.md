---
title: Использование инструкции (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-how-to
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7a0689e169fd968d8733b003f5d638d8c31c39b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="use-a-statement-odbc"></a>Использование инструкции (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-a-statement"></a>Использование инструкции  
  
1.  Для выделения дескриптора инструкции вызовите функцию [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с параметром *HandleType*, имеющим значение SQL_HANDLE_STMT.  
  
2.  Также можно вызвать [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для настройки параметров инструкции или [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) для получения атрибутов инструкции.  
  
     Чтобы использовать серверные курсоры, необходимо установить атрибуты курсоров в значения, отличные от значений по умолчанию.  
  
3.  Если инструкция будет выполняться несколько раз, то ее можно подготовить к выполнению с помощью функции [SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360).  
  
4.  Если инструкция имеет связанные маркеры параметров, можно привязать их к переменным программы с помощью функции [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md). Для подготовленной инструкции можно вызвать функции [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) и [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) to find the number и characteristics of the parameters.  
  
5.  Произведите прямое выполнение инструкции с помощью функции SQLExecDirect.  
  
     \- или -  
  
     Если инструкция была подготовлена, выполните ее несколько раз с помощью функции [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400).  
  
     \- или -  
  
     Вызовите функцию каталога, возвращающую результаты.  
  
6.  Обработайте результаты, связав столбцы результирующего набора с переменными программы, переместив данные из столбцов результирующего набора в переменные программы с помощью функции [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)или используя сочетание этих двух методов.  
  
     Произведите выборку из результирующего набора инструкции одной строки.  
  
     \- или -  
  
     Произведите выборку из результирующего набора нескольких строк с помощью блочного курсора.  
  
     \- или -  
  
     Вызовите функцию [SQLRowCount](../../../relational-databases/native-client-odbc-api/sqlrowcount.md) , чтобы определить число строк, затронутых инструкцией INSERT, UPDATE или DELETE.  
  
     Если инструкция SQL имеет несколько результирующих наборов, то после получения каждого результирующего набора вызовите функцию [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) , чтобы просмотреть, есть ли дополнительные результирующие наборы для обработки.  
  
7.  После обработки результатов, чтобы сделать для дескриптора инструкции доступной возможность выполнения новой инструкции, могут потребоваться следующие действия.  
  
    -   Если функция [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) не вызывалась до возвращения значения SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) для закрытия курсора.  
  
    -   Если маркеры параметров привязаны к переменным программы, то для их освобождения вызовите функцию [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметром *Option* , установленным в значение SQL_RESET_PARAMS.  
  
    -   Если столбцы результирующего набора привязаны к переменным программы, для их освобождения вызовите функцию [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметром *Option* , установленным в значение SQL_UNBIND.  
  
    -   Для повторного использования дескриптора инструкции перейдите к шагу 2.  
  
8.  Для освобождения дескриптора инструкции вызовите функцию [SQLFreeHandle](../../../relational-databases/native-client-odbc-api/sqlfreehandle.md) с параметром *HandleType*, установленным в значение SQL_HANDLE_STMT.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение инструкции запросов & #40; ODBC & #41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
