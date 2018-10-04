---
title: sys.Parameters (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.parameters_TSQL
- sys.parameters
- parameters
- parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameters catalog view
- table-valued parameters,sys.parameters
ms.assetid: 24e2764b-c8e5-4322-97a4-7407d8b8a92b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 33c87d4b784e46defac98823a5cf9d4dc9420aaa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752312"
---
# <a name="sysparameters-transact-sql"></a>sys.parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит строку для каждого параметра объекта, который принимает параметры. Если объект является скалярной функцией, также имеется одна строка, описывающая возвращаемое значение. Этой строки будет иметь **parameter_id** значение 0.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит этот параметр.|  
|**name**|**sysname**|Имя параметра. Уникален в пределах объекта.<br /><br /> Если объект является скалярной функцией, именем параметра будет пустая строка в строке, представляющей возвращаемое значение.|  
|**parameter_id**|**int**|Идентификатор параметра. Уникален в пределах объекта.<br /><br /> Если объект является скалярной функцией, **parameter_id** = 0 представляет возвращаемое значение.|  
|**system_type_id**|**tinyint**|Идентификатор системного типа параметра.|  
|**user_type_id**|**int**|Определенный пользователем идентификатор типа параметра.<br /><br /> Чтобы вернуть имя типа, присоедините к [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) представления по этому столбцу каталога.|  
|**max_length**|**smallint**|Максимальная длина параметра в байтах.<br /><br /> Значение = -1, если выбран тип данных столбца **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.|  
|**Точность**|**tinyint**|Для числового аргумента — точность; иначе 0.|  
|**Масштаб**|**tinyint**|Масштаб числового аргумента; иначе 0.|  
|**is_output**|**bit**|1 = выходной или возвращаемый параметр; иначе 0.|  
|**is_cursor_ref**|**bit**|1 = аргумент представляет собой ссылку на курсор.|  
|**has_default_value**|**bit**|1 = параметр имеет значение по умолчанию.<br /><br /> В данном представлении каталога [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всего лишь поддерживает значения по умолчанию для объектов среды CLR; поэтому этот столбец содержит значение 0 для объектов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Чтобы просмотреть значение по умолчанию параметра в [!INCLUDE[tsql](../../includes/tsql-md.md)] объекта, запрос **определение** столбец [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога или используйте [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)системной функции.|  
|**is_xml_document**|**bit**|1 = содержимое является готовым XML-документом.<br /><br /> 0 = содержимое является фрагментом документа, или тип данных столбца не **xml**.|  
|**default_value**|**sql_variant**|Если **has_default_value** равно 1, значение этого столбца значение по умолчанию для параметра; в противном случае — значение NULL.|  
|**xml_collection_id**|**int**|Ненулевое значение, если тип данных параметра **xml** и XML типизирован. Значением будет идентификатор коллекции, содержащей проверочное пространство имен схемы XML параметра.<br /><br /> 0 = нет коллекции схем XML.|  
|**is_readonly**|**bit**|1 = неизменяемый параметр; иначе 0.|  
|**is_nullable**|**bit**|1 = параметр допускает значение NULL. (по умолчанию).<br /><br /> 0 = параметр не допускает значения NULL для более эффективного выполнения компилируемых в собственном коде хранимых процедур.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)   
 [sys.system_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
