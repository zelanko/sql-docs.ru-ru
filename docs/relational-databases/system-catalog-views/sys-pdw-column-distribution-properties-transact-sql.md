---
title: sys.pdw_column_distribution_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b351139cb96ae58c114b57833d55ab97cce25a9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102225"
---
# <a name="syspdwcolumndistributionproperties-transact-sql"></a>sys.pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит данные о распространении для столбцов.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Идентификатор объекта, к которому относится столбец.||  
|**column_id**|**int**|Идентификатор столбца.||  
|**distribution_ordinal**|**tinyint**|Порядковый номер (начинающийся с 1) внутри набора распределения.|0 = столбец распределения. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] использует этот столбец для распределения родительской таблицы.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
