---
title: Использование курсоров (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: be512713462a9518856de2a16db749490ea24366
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306315"
---
# <a name="using-cursors-odbc"></a>Использование курсоров (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC поддерживает модель курсора, которая позволяет следующее.  
  
-   Несколько типов курсоров.  
  
-   Прокрутку и позиционирование в курсоре.  
  
-   Несколько параметров параллелизма.  
  
-   Позиционированные обновления.  
  
 Приложения ODBC редко декларируют и открывают курсоры или используют любые связанные с курсорами инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. ODBC автоматически открывает курсор для каждого возвращенного результирующего набора из инструкции SQL. Характеристики курсоров контролируются атрибутами оператора, установленными с [помощью S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) до выполнения оператора S'LLStmtAttr. Функции API ODBC для обработки результирующих наборов поддерживают полный набор функций работы с курсором, включая выборку, прокрутку и позиционированные обновления.  
  
 Далее приведено сравнение работы с курсорами в скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)] и приложениях ODBC.  
  
|Действие|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Определение режима работы курсоров|Указание через параметры DECLARE CURSOR|Установка атрибутов курсора с помощью [S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)|  
|Открытие курсора|ДЕКЛАРЕ КУРСОР *НОТ cursor_name*|**СЗЛЕсекПрямейл** или **СЗЛВы**|  
|Выборка строк|FETCH|**СЗЛУТ утвёй** или [СЗЛКОтСтовт](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|Позиционированное обновление|Предложение WHERE CURRENT OF для инструкции UPDATE или DELETE.|**функция SQLSetPos;**|  
|Закрытие курсора|БЛИЗКИЕ *CURSOR_NAME* DEALLOCATE|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 Серверные курсоры, реализованные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживают функции модели курсора ODBC. Драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует серверные курсоры для поддержки функций работы с курсорами API ODBC.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Способы реализации курсоров](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [Типы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [Режимы работы курсоров](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [Свойства курсора](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [Курзор Программирование Подробности &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [Прокрутка и выборка строк](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [Позиционированные обновления &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Родной клиент сервера &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [&#41;к &#40;«Трансакт-СЗЛ»](../../t-sql/language-elements/close-transact-sql.md)   
 [Курсоры](../../relational-databases/cursors.md)   
 [&#41;&#40;ДЕКАТЕЛ](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [ДЕКЛАРЕ КУРСОР &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [FETCH &#40;&#41;«Трансакт-СЗЛ»](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)  
  
  
