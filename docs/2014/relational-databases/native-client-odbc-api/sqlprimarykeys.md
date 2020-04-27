---
title: SQLPrimaryKeys | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a12392f9e70fec2fae3b7790b43f12779b8868b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046698"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Таблица может содержать столбец или столбцы, которые могут использоваться в качестве уникальных идентификаторов строк, а таблицы, созданные без ограничения ПЕРВИЧного ключа, возвращают пустой результирующий набор для SQLPrimaryKeys. Функция ODBC [SQLSpecialColumns](sqlspecialcolumns.md) сообщает кандидатов идентификаторов строк для таблиц без первичных ключей.  
  
 SQLPrimaryKeys возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName*, *SchemaName*или *TableName* . Функция SQLFetch возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 SQLPrimaryKeys может выполняться на статическом серверном курсоре. Попытка выполнить SQLPrimaryKeys для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys будет возвращать сведения о первичных ключевых столбцах табличных типов. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLPrimaryKeys](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
