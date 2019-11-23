---
title: SQLPrimaryKeys | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c2ee83335e00c3129d73c26db37d40af2375c410
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786048"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Таблица может содержать столбец или столбцы, которые могут использоваться в качестве уникальных идентификаторов строк, а таблицы, созданные без ограничения ПЕРВИЧного ключа, возвращают пустой результирующий набор для SQLPrimaryKeys. Функция ODBC [SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) сообщает кандидатов идентификаторов строк для таблиц без первичных ключей.  
  
 SQLPrimaryKeys возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName*, *SchemaName*или *TableName* . SQLFetch возвращает SQL_NO_DATA, если в этих параметрах используются недопустимые значения.  
  
 SQLPrimaryKeys может выполняться на статическом серверном курсоре. Попытка выполнить SQLPrimaryKeys для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys будет возвращать сведения о первичных ключевых столбцах табличных типов. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также статью  
   [функции SQLPrimaryKeys](https://go.microsoft.com/fwlink/?LinkId=59361)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
