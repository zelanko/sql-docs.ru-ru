---
title: СЗЛТаблицы Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f3fa2b053c41facba7d608b2352772abd3ff103
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291797"
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  S'LTables могут быть выполнены на статическом курсоре сервера. Попытка выполнить S'LTables на курсоре updatable (динамическом или клавиатуре) вернет SQL_SUCCESS_WITH_INFO, указывающий на изменение типа курсора.  
  
 S'LTables сообщает таблицы из всех баз данных, когда параметр *CatalogName* SQL_ALL_CATALOGS а все остальные параметры содержат значения по умолчанию (указатели NULL).  
  
 Для сообщения о доступных каталогах, схемах и типах таблиц, S'LTables специально использует пустые строки (указатели нулевой длины byte). Пустые строки не являются значениями по умолчанию (указатели NULL).  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
 S'LTables возвращает информацию о любых таблицах, имена которых совпадают с *TableName* и принадлежат текущему пользователю.  
  
## <a name="sqltables-and-table-valued-parameters"></a>Функция SQLTables и возвращающие табличное значение параметры  
 Когда атрибут оператора SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, S'LTables возвращает информацию о типах таблиц. Значение TABLE_TYPE, возвращенное для типа таблицы в столбце 4 набора результатов, возвращенного S'LTables, — это TABLE TYPE. Для получения более подробной информации о SQL_SOPT_SS_NAME_SCOPE, [см.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
 Таблицы, представления и синонимы имеют общее пространство имен, отличающееся от пространства имен табличных типов. Хотя таблица и представление не могут иметь одинаковое имя, в одном каталоге и схеме можно иметь таблицу и табличный тип с одинаковым именем.  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="example"></a>Пример  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LTables](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
