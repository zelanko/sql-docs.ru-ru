---
title: Метаданные TVP для подготовленных инструкций
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 27ae8ffe9fc719e751511b9930889e1fc265d876
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75241850"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Метаданные возвращающего табличное значение параметра для подготовленных инструкций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Приложение может получать метаданные для вызова подготовленной процедуры через SQLNumParams и SQLDescribeParam. Для возвращающих табличные значения параметров *дататипептр* имеет значение SQL_SS_TABLE. Дополнительные метаданные доступны через SQLGetDescField для SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME и SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME и SQL_CA_SS_SCHEMA_NAME можно использовать с SQLColumns для получения метаданных столбца для табличных типов, связанных с параметрами, возвращающими табличное значение. В этом случае SQL_SOPT_SS_NAME_SCOPE должно быть установлено в SQL_SS_NAME_SCOPE_TABLE_TYPE перед вызовом SQLColumns. После получения метаданных столбца, соответствующего возвращающему табличное значение параметру, параметр SQL_SOPT_SS_NAME_SCOPE необходимо установить обратно в значение по умолчанию — SQL_SS_NAME_SCOPE_TABLE.  
  
 Параметры SQL_CA_SS_TYPE_NAME, SQL_CA_SS_TYPE_CATALOG_NAME и SQL_CA_SS_TYPE_SCHEMA_NAME также могут использоваться с параметрами определяемых пользователем типов данных CLR.  
  
 Для подготовленных инструкций, не являющихся вызовами хранимых процедур, нельзя получить метаданные возвращающего табличные значения параметра. При попытке выполнения данного действия приложение возвращает ошибку SQL_ERROR с кодом SQLSTATE 42000 и сообщение «Синтаксическая ошибка или нарушение доступа».  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
