---
title: Создание инструкций SQL для курсоров | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c472fac6b4cf6f138fb75beeab8933c40e08993
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="constructing-sql-statements-for-cursors"></a>Конструирование инструкций SQL для курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента использует серверные курсоры для реализации функциональности курсоров, определенных в спецификации ODBC. Приложение ODBC управляет поведением курсора с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) Чтобы задать различные атрибуты инструкций. К ним относятся атрибуты и их значения по умолчанию.  
  
|Attribute|По умолчанию|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Если эти параметры заданы значения по умолчанию во время выполнения инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не использует серверный курсор для реализации результирующего набора; вместо этого он использует результирующий набор по умолчанию. Если все эти параметры были изменены из значения по умолчанию во время выполнения инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента пытается использовать серверный курсор для реализации результирующего набора.  
  
 Результирующие наборы по умолчанию поддерживают все инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ограничения на типы инструкций SQL, которые можно выполнять при использовании результирующего набора по умолчанию, отсутствуют.  
  
 Серверные курсоры поддерживают не все инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Серверные курсоры не поддерживают любые инструкции SQL, формирующие множественные результирующие наборы.  
  
 Следующие типы инструкций не поддерживаются серверными курсорами.  
  
-   Пакеты  
  
     Инструкции SQL, состоящие из двух и более отдельных инструкций SQL SELECT, например:  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   Хранимые процедуры с несколькими инструкциями SELECT  
  
     Инструкции SQL, которые выполняют хранимую процедуру, содержащую более одной инструкции SELECT. К ним относятся инструкции SELECT, которые заполняют параметры или переменные.  
  
-   Ключевые слова  
  
     Инструкции SQL, которые содержат ключевые слова FOR BROWSE или INTO.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: если инструкция SQL, соответствующая любому из этих условий, выполняется с серверным курсором, то серверный курсор неявно преобразуется в результирующий набор по умолчанию. После **SQLExecDirect** или **SQLExecute** возвращает SQL_SUCCESS_WITH_INFO, курсор атрибуты настройки будут возвращены к значениям по умолчанию.  
  
 Инструкции SQL, не относящиеся к перечисленным выше категориям, могут выполняться с любыми настройками атрибутов инструкций; они работают одинаково успешно с результирующим набором по умолчанию и с серверным курсором.  
  
## <a name="errors"></a>ошибки  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 и более поздних версиях попытка выполнить инструкцию, возвращающую несколько результирующих наборов, формирует SQL_SUCCESS_WITH_INFO и следующее сообщение:  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 Приложения ODBC, получающей это сообщение можно вызвать [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) определить текущие настройки курсора.  
  
 При попытке выполнить процедуру с несколькими инструкциями SELECT с использованием серверных курсоров формируется следующая ошибка:  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 При попытке выполнить пакет с несколькими инструкциями SELECT с использованием серверных курсоров формируется следующая ошибка:  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 Приложения ODBC, получающие эти ошибки, должны сбросить все атрибуты инструкции курсора в их значения по умолчанию перед попыткой выполнить инструкцию.  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
