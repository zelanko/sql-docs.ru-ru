---
title: Конструирование инструкций SQL для курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5bfb18fea7b36236ad571dbd9b39301069fb00fc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717912"
---
# <a name="constructing-sql-statements-for-cursors"></a>Конструирование инструкций SQL для курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента использует серверные курсоры для реализации функциональности курсоров, определенных в спецификации ODBC. Приложение ODBC управляет режимом работы курсоров с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) задать различные атрибуты инструкций. К ним относятся атрибуты и их значения по умолчанию.  
  
|attribute|По умолчанию|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Если эти параметры заданы значения по умолчанию во время выполнения инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не использует серверный курсор для реализации результирующего набора; вместо этого он использует результирующий набор по умолчанию. Если любой из этих вариантов изменяются настройки по умолчанию во время выполнения инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента пытается использовать серверный курсор для реализации результирующего набора.  
  
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
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: если инструкция SQL, соответствующая любому из этих условий, выполняется с серверным курсором, то серверный курсор неявно преобразуется в результирующий набор по умолчанию. После **SQLExecDirect** или **SQLExecute** возвращает значение SQL_SUCCESS_WITH_INFO, курсора присваиваются атрибуты к параметрам по умолчанию.  
  
 Инструкции SQL, не относящиеся к перечисленным выше категориям, могут выполняться с любыми настройками атрибутов инструкций; они работают одинаково успешно с результирующим набором по умолчанию и с серверным курсором.  
  
## <a name="errors"></a>ошибки  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 и более поздних версиях попытка выполнить инструкцию, возвращающую несколько результирующих наборов, формирует SQL_SUCCESS_WITH_INFO и следующее сообщение:  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 Приложения ODBC, получающие это сообщение можно вызвать [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) для определения текущих параметров курсора.  
  
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
  
  
