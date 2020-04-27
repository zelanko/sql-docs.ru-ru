---
title: Использование оператора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 842e862dff7eca85a05df0222989c6ee6390ab89
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63200324"
---
# <a name="use-a-statement-odbc"></a>Использование инструкции (ODBC)
    
### <a name="to-use-a-statement"></a>Использование инструкции  
  
1.  Для выделения дескриптора инструкции вызовите функцию [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) с параметром *HandleType*, имеющим значение SQL_HANDLE_STMT.  
  
2.  Также можно вызвать [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) для настройки параметров инструкции или [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) для получения атрибутов инструкции.  
  
     Чтобы использовать серверные курсоры, необходимо установить атрибуты курсоров в значения, отличные от значений по умолчанию.  
  
3.  Если инструкция будет выполняться несколько раз, то ее можно подготовить к выполнению с помощью функции [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360).  
  
4.  Если инструкция имеет связанные маркеры параметров, можно привязать их к переменным программы с помощью функции [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md). Для подготовленной инструкции можно вызвать функции [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) и [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number и characteristics of the parameters.  
  
5.  Произведите прямое выполнение инструкции с помощью функции SQLExecDirect.  
  
     \- или -  
  
     Если инструкция была подготовлена, выполните ее несколько раз с помощью функции [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400).  
  
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
 [Инструкции по выполнению запросов &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
