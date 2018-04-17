---
title: Использование курсоров (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ac185851afe65ffd5b759e7176a2d98a2259287a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-cursors-odbc"></a>Использование курсоров (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC поддерживает модель курсора, которая позволяет следующее.  
  
-   Несколько типов курсоров.  
  
-   Прокрутку и позиционирование в курсоре.  
  
-   Несколько параметров параллелизма.  
  
-   Позиционированные обновления.  
  
 Приложения ODBC редко декларируют и открывают курсоры или используют любые связанные с курсорами инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. ODBC автоматически открывает курсор для каждого возвращенного результирующего набора из инструкции SQL. Характеристики курсоров управляются атрибуты инструкции с [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) перед SQL выполняется инструкция. Функции API ODBC для обработки результирующих наборов поддерживают полный набор функций работы с курсором, включая выборку, прокрутку и позиционированные обновления.  
  
 Далее приведено сравнение работы с курсорами в скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)] и приложениях ODBC.  
  
|Действие|[!INCLUDE[tsql](../../includes/tsql-md.md)]|интерфейс ODBC|  
|------------|------------------------|----------|  
|Определение режима работы курсоров|Указание через параметры DECLARE CURSOR|Присвоить атрибутам курсора с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)|  
|Открытие курсора|DECLARE CURSOR OPEN *cursor_name*|**SQLExecDirect** или **SQLExecute**|  
|Выборка строк|FETCH|**SQLFetch** или [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|Позиционированное обновление|Предложение WHERE CURRENT OF для инструкции UPDATE или DELETE.|**SQLSetPos**|  
|Закрытие курсора|ЗАКРЫТЬ *cursor_name* DEALLOCATE|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 Серверные курсоры, реализованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживают функции модели курсора ODBC. Драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует серверные курсоры для поддержки функций работы с курсорами API ODBC.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Способы реализации курсоров](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [Типы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [Режим работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [Свойства курсора](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [Подробные сведения о программировании курсоров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [Прокрутка и выборка строк](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [Позиционированные обновления &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE (Transact-SQL)](../../t-sql/language-elements/close-transact-sql.md)   
 [Курсоры](../../relational-databases/cursors.md)   
 [DEALLOCATE (Transact-SQL)](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [FETCH (Transact-SQL)](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)  
  
  
