---
title: sys. numbered_procedure_parameters (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- numbered_procedure_parameters_TSQL
- sys.numbered_procedure_parameters_TSQL
- numbered_procedure_parameters
- sys.numbered_procedure_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedure_parameters catalog view
ms.assetid: a441d46d-1f30-41c2-8d94-e9442f59786e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 91deff0aa45038c22ece0f34b02314c2bf8e4d14
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760334"
---
# <a name="sysnumbered_procedure_parameters-transact-sql"></a>sys.numbered_procedure_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Содержит по одной строке на каждый аргумент нумерованной процедуры. При создании нумерованных хранимых процедур базовая процедура имеет номер 1. Все последующие процедуры получают номера 2, 3 и т. д. **sys. numbered_procedure_parameters** содержит определения параметров для всех последующих процедур с номерами 2 и выше. Это представление не отображает аргументы базовой хранимой процедуры (процедуры с номером 1). Базовая хранимая процедура подобна ненумерованным хранимым процедурам. Поэтому его параметры представлены в [представлении sys. parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md).  
  
> [!IMPORTANT]  
>  Пронумерованные процедуры являются устаревшими. Использование нумерованных процедур не рекомендуется. При компиляции запроса, использующего это представление каталога, инициируется событие DEPRECATION_ANNOUNCEMENT.  
  
> [!NOTE]  
>  Аргументы, связанные с языком XML и средой CLR, для нумерованных процедур не поддерживаются.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит этот параметр.|  
|**procedure_number**|**smallint**|Номер этой процедуры в данном объекте (2 или больше).|  
|**name**|**sysname**|Имя параметра. Уникален в пределах **procedure_number**.|  
|**parameter_id**|**int**|Идентификатор параметра. Уникален в пределах **procedure_number**.|  
|**system_type_id**|**tinyint**|Идентификатор системного типа аргумента.|  
|**user_type_id**|**int**|Идентификатор определяемого пользователем типа аргумента.|  
|**max_length**|**smallint**|Максимальная длина аргумента в байтах.<br /><br /> -1 = тип данных столбца: varchar(max), nvarchar(max) или varbinary(max).|  
|**precision**|**tinyint**|Для числового аргумента — точность; иначе 0.|  
|**масштаб**|**tinyint**|Масштаб числового аргумента; иначе 0.|  
|**is_output**|**bit**|1 = аргумент помечен как OUTPUT или RETURN; иначе 0|  
|**is_cursor_ref**|**bit**|1 = аргумент представляет собой ссылку на курсор.|  
  
> [!NOTE]  
>  Аргументы, связанные с языком XML и средой CLR, для нумерованных процедур не поддерживаются.  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
