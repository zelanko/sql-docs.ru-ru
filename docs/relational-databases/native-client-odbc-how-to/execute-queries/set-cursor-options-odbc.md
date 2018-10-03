---
title: Указание параметров курсора (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6bf8a5002c67ee236075efc0a06d5422f03cf398
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638482"
---
# <a name="set-cursor-options-odbc"></a>Указание параметров курсора (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Чтобы задать параметры курсора, вызовите [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) для задания или [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) для получения параметров инструкции, которые управляют поведением курсора.  
  
|*Attribute*|Указывает|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|Однопроходный, статический, динамический или управляемый набором ключей тип курсора|  
|SQL_ATTR_CONCURRENCY|Параметр управления параллелизмом – только для чтения, блокирующий, оптимистичный с использованием отметок времени или оптимистичный с использованием значений|  
|SQL_ATTR_ROW_ARRAY_SIZE|Количество строк, получаемых в каждой выборке|  
|SQL_ATTR_CURSOR_SENSITIVITY|Курсор, который отображает или не отображает обновления строк курсора, выполняемые в других соединениях|  
|SQL_ATTR_CURSOR_SCROLLABLE|Курсор, который может прокручиваться вперед и назад|  
  
 Значения по умолчанию для этих атрибутов (однопроходный, только для чтения, размер набора строк, равный 1) не используют серверные курсоры. Для использования серверных курсоров по крайней мере одному из этих атрибутов должно быть задано значение, отличное от значения по умолчанию, а выполняемая инструкция должна быть единственной инструкцией SELECT или хранимой процедурой, содержащей единственную инструкцию SELECT. При использовании серверных курсоров инструкции SELECT нельзя использовать предложения, не поддерживается серверными курсорами: COMPUTE, COMPUTE BY, FOR BROWSE и INTO.  
  
 Используемым типом курсора можно управлять, установив SQL_ATTR_CURSOR_TYPE и SQL_ATTR_CONCURRENCY или установив SQL_ATTR_CURSOR_SENSITIVITY и SQL_ATTR_CURSOR_SCROLLABLE. Не следует смешивать два метода задания режима работы курсоров.  
  
## <a name="example"></a>Пример  
 В следующем образце выделяется дескриптор инструкции, устанавливается динамический тип курсора и оптимистический параллелизм с управлением версиями строк, а затем выполняется инструкция SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>Пример  
 В следующем образце выделяется дескриптор инструкции, устанавливается прокручиваемый, чувствительный курсор, а затем выполняется инструкция SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>См. также  
 [Выполнении запросов разделы руководства, посвященные &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
