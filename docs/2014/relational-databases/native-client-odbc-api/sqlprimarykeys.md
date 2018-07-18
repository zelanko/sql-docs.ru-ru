---
title: SQLPrimaryKeys | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e0e7ae6624bba3866796a3aa457e510abb26826
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423743"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Таблица может содержать столбец или столбцы, которые служат уникальными идентификаторами строк и таблицы, созданные без ограничения PRIMARY KEY возвращает пустой результирующий набор для SQLPrimaryKeys. Функции ODBC [SQLSpecialColumns](sqlspecialcolumns.md) отчеты строки идентификатора кандидатами для таблицы без первичных ключей.  
  
 SQLPrimaryKeys возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *SchemaName*, или *TableName* параметров. SQLFetch возвращает значение SQL_NO_DATA, если в этих параметров используются недопустимые значения.  
  
 SQLPrimaryKeys могут быть выполнены для статического серверного курсора. При попытке выполнить SQLPrimaryKeys для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, определяющий, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя для *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys возвращает сведения о первичных ключевых столбцов табличных типов. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLPrimaryKeys](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
