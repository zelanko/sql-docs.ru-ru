---
title: Использование курсоров (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc53253c93f5f52c6bbe00941eadbf14b65d5f64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206818"
---
# <a name="using-cursors-odbc"></a>Использование курсоров (ODBC)
  ODBC поддерживает модель курсора, которая позволяет следующее.  
  
-   Несколько типов курсоров.  
  
-   Прокрутку и позиционирование в курсоре.  
  
-   Несколько параметров параллелизма.  
  
-   Позиционированные обновления.  
  
 Приложения ODBC редко декларируют и открывают курсоры или используют любые связанные с курсорами инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. ODBC автоматически открывает курсор для каждого возвращенного результирующего набора из инструкции SQL. Характеристики курсоров управляются атрибуты инструкции, набор с [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) перед SQL выполняется инструкция. Функции API ODBC для обработки результирующих наборов поддерживают полный набор функций работы с курсором, включая выборку, прокрутку и позиционированные обновления.  
  
 Далее приведено сравнение работы с курсорами в скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)] и приложениях ODBC.  
  
|Action|[!INCLUDE[tsql](../../includes/tsql-md.md)]|интерфейс ODBC|  
|------------|------------------------|----------|  
|Определение режима работы курсоров|Указание через параметры DECLARE CURSOR|Присвоить атрибутам курсора с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|Открытие курсора|DECLARE CURSOR OPEN *cursor_name*|**SQLExecDirect** или **SQLExecute**|  
|Выборка строк|FETCH|**SQLFetch** или [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|Позиционированное обновление|Предложение WHERE CURRENT OF для инструкции UPDATE или DELETE.|**SQLSetPos**|  
|Закрытие курсора|ЗАКРЫТЬ *cursor_name* DEALLOCATE|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 Серверные курсоры, реализованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживают функции модели курсора ODBC. Драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует серверные курсоры для поддержки функций работы с курсорами API ODBC.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Способы реализации курсоров](implementation/how-cursors-are-implemented.md)  
  
-   [Типы курсоров](cursor-types.md)  
  
-   [Режимы работы курсоров](cursor-behaviors.md)  
  
-   [Свойства курсора](properties/cursor-properties.md)  
  
-   [Подробные сведения о программировании курсоров &#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [Прокрутка и выборка строк](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Позиционированные обновления &#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE (Transact-SQL)](/sql/t-sql/language-elements/close-transact-sql)   
 [Курсоры](../../relational-databases/cursors.md)   
 [DEALLOCATE (Transact-SQL)](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [DECLARE CURSOR (Transact-SQL)](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [FETCH (Transact-SQL)](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN (Transact-SQL)](/sql/t-sql/language-elements/open-transact-sql)  
  
  
