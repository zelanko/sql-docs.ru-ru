---
title: sys.syscharsets (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscharsets
- syscharsets
- sys.syscharsets_TSQL
- syscharsets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscharsets system table
- sys.syscharsets compatibility view
ms.assetid: f16d987c-bd19-4668-9ef7-785b8fb9ff5b
caps.latest.revision: 42
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6ae1eb1439decfdf5c42d42f42c1063916f551ac
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562858"
---
# <a name="syssyscharsets-transact-sql"></a>sys.syscharsets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждой кодировки и порядок сортировки, определенный для использования в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Один из порядков сортировки помечен в **sysconfigures** как порядок сортировки по умолчанию. Это единственный используется в действительности.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**type**|**smallint**|Тип сущности, представляемый этой строкой.<br /><br /> 1001 = кодировка.<br /><br /> 2001 = порядок сортировки.|  
|**идентификатор**|**tinyint**|Уникальный идентификатор для кодировки или порядка сортировки. Обратите внимание на то, что у порядков сортировки и кодировок не может быть одного и того же общего идентификатора. Идентификаторы в диапазоне от 1 до 240 зарезервированы для использования в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|**csid**|**tinyint**|Если строка представляет кодировку, это поле остается неиспользованным. Если строка представляет порядок сортировки, в этом поле содержится идентификатор кодировки, на котором построен данный порядок сортировки. Предполагается, что в таблице содержится строка кодировки с данным идентификатором.|  
|**status**|**smallint**|Биты данных о внутреннем состоянии системы.|  
|**name**|**sysname**|Уникальное имя для кодировки или порядка сортировки. Это поле должно содержать только буквы A–Z или a–z, цифры 0–9, символ подчеркивания (_) и должно начинаться с буквы.|  
|**Описание**|**nvarchar(255)**|Необязательное описание характеристик кодировки или порядка сортировки.|  
|**binarydefinition**|**varbinary(6000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Определение**|**image**|Уникальное описание для кодировки или порядка сортировки. Структура данных в этом поле зависит от типа.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
