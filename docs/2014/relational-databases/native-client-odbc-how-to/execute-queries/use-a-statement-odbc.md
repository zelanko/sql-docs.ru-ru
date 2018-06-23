---
title: Использование инструкции (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 50a4f012b556bb6f54a0b9e672c2f9ff16a44fd2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086679"
---
# <a name="use-a-statement-odbc"></a>Использование инструкции (ODBC)
    
### <a name="to-use-a-statement"></a>Использование инструкции  
  
1.  Для выделения дескриптора инструкции вызовите функцию [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с параметром *HandleType*, имеющим значение SQL_HANDLE_STMT.  
  
2.  Также можно вызвать [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) для настройки параметров инструкции или [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) для получения атрибутов инструкции.  
  
     Чтобы использовать серверные курсоры, необходимо установить атрибуты курсоров в значения, отличные от значений по умолчанию.  
  
3.  Если инструкция будет выполняться несколько раз, то ее можно подготовить к выполнению с помощью функции [SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360).  
  
4.  Если инструкция имеет связанные маркеры параметров, можно привязать их к переменным программы с помощью функции [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md). Для подготовленной инструкции можно вызвать функции [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) и [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number и characteristics of the parameters.  
  
5.  Произведите прямое выполнение инструкции с помощью функции SQLExecDirect.  
  
     \- или -  
  
     Если инструкция была подготовлена, выполните ее несколько раз с помощью функции [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400).  
  
     \- или -  
  
     Вызовите функцию каталога, возвращающую результаты.  
  
6.  Обработайте результаты, связав столбцы результирующего набора с переменными программы, переместив данные из столбцов результирующего набора в переменные программы с помощью функции [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)или используя сочетание этих двух методов.  
  
     Произведите выборку из результирующего набора инструкции одной строки.  
  
     \- или -  
  
     Произведите выборку из результирующего набора нескольких строк с помощью блочного курсора.  
  
     \- или -  
  
     Вызовите функцию [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) , чтобы определить число строк, затронутых инструкцией INSERT, UPDATE или DELETE.  
  
     Если инструкция SQL имеет несколько результирующих наборов, то после получения каждого результирующего набора вызовите функцию [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) , чтобы просмотреть, есть ли дополнительные результирующие наборы для обработки.  
  
7.  После обработки результатов, чтобы сделать для дескриптора инструкции доступной возможность выполнения новой инструкции, могут потребоваться следующие действия.  
  
    -   Если функция [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) не вызывалась до возвращения значения SQL_NO_DATA, вызовите функцию [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) для закрытия курсора.  
  
    -   Если маркеры параметров привязаны к переменным программы, то для их освобождения вызовите функцию [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) с параметром *Option* , установленным в значение SQL_RESET_PARAMS.  
  
    -   Если столбцы результирующего набора привязаны к переменным программы, для их освобождения вызовите функцию [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) с параметром *Option* , установленным в значение SQL_UNBIND.  
  
    -   Для повторного использования дескриптора инструкции перейдите к шагу 2.  
  
8.  Для освобождения дескриптора инструкции вызовите функцию [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) с параметром *HandleType*, установленным в значение SQL_HANDLE_STMT.  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов инструкции &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  