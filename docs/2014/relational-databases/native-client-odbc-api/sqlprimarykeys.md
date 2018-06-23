---
title: SQLPrimaryKeys | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb0dc440025730c278206a751a5ce741b69b0f6e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095926"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Таблица может содержать столбец или столбцы, которые могут служить уникальными идентификаторами строк и таблицы, созданные без ограничения PRIMARY KEY возвращает пустой результирующий набор для SQLPrimaryKeys. Функция ODBC [SQLSpecialColumns](sqlspecialcolumns.md) отчеты строк идентификатор кандидатами для таблицы без первичных ключей.  
  
 SQLPrimaryKeys возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *SchemaName*, или *TableName* параметров. SQLFetch возвращает значение SQL_NO_DATA, если в этих параметров используются недопустимые значения.  
  
 SQLPrimaryKeys может выполняться для статического серверного курсора. Попытка выполнить SQLPrimaryKeys для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys возвращает сведения о первичных ключевых столбцов для табличных типов. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLPrimaryKeys](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  