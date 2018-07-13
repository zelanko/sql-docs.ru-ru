---
title: Дополнительный параметр Table-Valued метаданных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f28c5baf528a975b987c68e81543932b63dc5761
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419753"
---
# <a name="additional-table-valued-parameter-metadata"></a>Дополнительные метаданные возвращающего табличное значение параметра
  Чтобы получить метаданные для возвращающих табличные значения параметра, приложение вызывает SQLProcedureColumns. Для возвращающих табличные значения параметра SQLProcedureColumns возвращает одну строку. Два дополнительных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-определенные столбцы, столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME, были добавлены для предоставления сведений о схеме и каталоге для табличных типов, связанных с возвращающих табличное значение параметрами. В соответствии со спецификацией ODBC столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME находятся перед столбцами, зависящими от драйвера, добавленными в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и после всех столбцов, обязательных для ODBC.  
  
 В следующей таблице приводится список столбцов, имеющих отношение к возвращаемым табличное значение параметрам.  
  
|Имя столбца|Тип данных|Значения/комментарии|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint, не NULL|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar(128), не NULL|Имя типа возвращающего табличное значение параметра.|  
|COLUMN_SIZE|Целочисленный|NULL|  
|BUFFER_LENGTH|Целочисленный|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint, не NULL|SQL_NULLABLE|  
|REMARKS|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint, не NULL|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Целочисленный|NULL|  
|ORDINAL_POSITION|Integer, не NULL|Порядковый номер параметра.|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar(128), не NULL|Каталог, содержащий определение табличного типа для возвращающего табличное значение параметра.|  
|SS_TYPE_SCHEMA_NAME|WVarchar(128), не NULL|Схема, содержащая определение табличного типа для возвращающего табличное значение параметра.|  
  
 Столбцы типа WVarchar в спецификации ODBC определяются как тип Varchar, но в действительности во всех последних драйверах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC возвращаются как WVarchar. Это изменение было сделано, когда к спецификации ODBC 3.5 была добавлена поддержка Юникода, но оно не описано.  
  
 Чтобы получить дополнительные метаданные для возвращающих табличные значения параметров, приложение использует функции каталога SQLColumns и SQLPrimaryKeys. Перед вызовом этих функций для возвращающих табличное значение параметров приложение должно присвоить атрибуту инструкции SQL_SOPT_SS_NAME_SCOPE значение SQL_SS_NAME_SCOPE_TABLE_TYPE. Оно указывает, что приложению требуются метаданные возвращающего табличное значение типа, а не таблицы. Затем приложение передает TYPE_NAME, возвращающих табличные значения параметра, как *TableName* параметра. Столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME используются с *CatalogName* и *SchemaName* параметров, соответственно, для определения каталога и схемы для возвращающих табличные значения параметра. Когда приложение закончит получать метаданные для возвращающего табличное значение параметра, оно должно вновь присвоить SQL_SOPT_SS_NAME_SCOPE значение по умолчанию SQL_SS_NAME_SCOPE_TABLE.  
  
 Если SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE, то запросы к связанным серверам завершаются ошибкой. Вызов SQLColumns или SQLPrimaryKeys с каталог, содержащий серверный компонент завершается с ошибкой.  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
