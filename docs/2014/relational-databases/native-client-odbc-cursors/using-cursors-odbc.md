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
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020462"
---
# <a name="using-cursors-odbc"></a>Использование курсоров (ODBC)
  ODBC поддерживает модель курсора, которая позволяет следующее.  
  
-   Несколько типов курсоров.  
  
-   Прокрутку и позиционирование в курсоре.  
  
-   Несколько параметров параллелизма.  
  
-   Позиционированные обновления.  
  
 Приложения ODBC редко декларируют и открывают курсоры или используют любые связанные с курсорами инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. ODBC автоматически открывает курсор для каждого возвращенного результирующего набора из инструкции SQL. Характеристики курсоров контролируются атрибутами инструкции, заданными с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) , перед выполнением инструкции SQL. Функции API ODBC для обработки результирующих наборов поддерживают полный набор функций работы с курсором, включая выборку, прокрутку и позиционированные обновления.  
  
 Далее приведено сравнение работы с курсорами в скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)] и приложениях ODBC.  
  
|Действие|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Определение режима работы курсоров|Указание через параметры DECLARE CURSOR|Установка атрибутов курсора с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|Открытие курсора|ОБЪЯВЛЕНИЕ открытого КУРСОРа *cursor_name*|**SQLExecDirect** или **SQLExecute**|  
|Выборка строк|FETCH|**SQLFetch** или [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|Позиционированное обновление|Предложение WHERE CURRENT OF для инструкции UPDATE или DELETE.|**функция SQLSetPos;**|  
|Закрытие курсора|ЗАКРЫТЬ *CURSOR_NAME* освободить|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 Серверные курсоры, реализованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживают функции модели курсора ODBC. Драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует серверные курсоры для поддержки функций работы с курсорами API ODBC.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Способы реализации курсоров](implementation/how-cursors-are-implemented.md)  
  
-   [Типы курсоров](cursor-types.md)  
  
-   [Режимы работы курсоров](cursor-behaviors.md)  
  
-   [Свойства курсора](properties/cursor-properties.md)  
  
-   [Сведения о программировании курсора &#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [Прокрутка и выборка строк](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Позиционированные обновления &#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [ЗАКРЫТЬ &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql)   
 [Курсоры](../../relational-databases/cursors.md)   
 [ОСВОБОЖДЕНИЕ &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [ОБЪЯВИТь курсор &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [ПОЛУЧЕНИЕ &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN (Transact-SQL)](/sql/t-sql/language-elements/open-transact-sql)  
  
  
