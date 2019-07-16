---
title: sys.sequences (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sequences_TSQL
- sys.sequences
- sequences
- sequences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sys. sequences catalog view
- sys.sequences catalog view
ms.assetid: 0e1b0e32-1cce-40f7-83c8-860ec660138a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 410f6dcca93614c42de4a703fd591bb1c9cbc59a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060547"
---
# <a name="syssequences-transact-sql"></a>sys.sequences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит строку для каждого объекта последовательности в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|\<наследуемые столбцы >||Наследует все столбцы из [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**start_value**|**sql_variant NOT NULL**|Стартовое значение для объекта последовательности. Если объект последовательности перезапускается с помощью инструкции ALTER SEQUENCE, он начинается с этого значения. Когда объект последовательности циклов он переходит к **minimum_value** или **maximum_value**, а не **start_value**.|  
|**increment**|**sql_variant NOT NULL**|Значение, на которое увеличивается значение объекта последовательности после каждого созданного значения.|  
|**minimum_value**|**sql_variant NULL**|Минимальное значение, возвращаемое объектом последовательности. По достижении этого значения объект последовательности либо возвращает ошибку при попытке создать дополнительные значения, либо перезапускается, если для него указан параметр CYCLE. Если нет MINVALUE не задан, этот столбец возвращает минимальное значение, допустимое типом данных генератора последовательности.|  
|**maximum_value**|**sql_variant NULL**|Максимальное значение, возвращаемое объектом последовательности. По достижении этого значения объект последовательности либо начинает возвращать ошибку при попытке создать дополнительные значения, либо перезапускается, если для него указан параметр CYCLE. Если параметр MAXVALUE не задан, этот столбец возвращает максимальное значение, допустимое типом данных объекта последовательности.|  
|**is_cycling**|**бит NOT NULL**|Возвращает значение 0, если для объекта последовательности указан параметр NO CYCLE, и 1, если указан параметр CYCLE.|  
|**is_cached**|**бит NOT NULL**|Возвращает значение 0, если для объекта последовательности указан параметр NO CACHE, и 1, если указан параметр CACHE.|  
|**cache_size**|**int NULL**|Возвращает заданный размер кэша для объекта последовательности. Этот столбец содержит значение NULL, если последовательность была создана с параметром NO CACHE или был указан параметр CACHE без указания размера кэша. Если значение cache_size больше максимального числа значений, которые может возвращать объект последовательности, все равно показывается такой недостижимый размер кэша.|  
|**system_type_id**|**tinyint NOT NULL**|Идентификатор системного типа для типа данных объекта последовательности.|  
|**user_type_id**|**int NOT NULL**|Определенный пользователем идентификатор типа данных для объекта последовательности.|  
|**precision**|**tinyint NOT NULL**|Максимальная точность типа данных.|  
|**масштаб**|**tinyint NOT NULL**|Максимальный масштаб типа данных. Масштаб возвращается вместе с точностью для предоставления пользователю полных метаданных. Масштаб объектов последовательности всегда равен 0, поскольку для них допустимы только целочисленные типы.|  
|**Текущее значение**|**sql_variant NOT NULL**|Последнее предоставленное значение. То есть значение, возвращаемое из последнего выполнения функции NEXT VALUE FOR или последнее значение выполнения **sp_sequence_get_range** процедуры. Если последовательность не использовалась, возвращается значение START WITH.|  
|**is_exhausted**|**бит NOT NULL**|0 указывает, что последовательность еще может предоставлять новые значения. 1 указывает, что объект последовательности достиг значения MAXVALUE и для последовательности не задан параметр CYCLE. Функция NEXT VALUE FOR будет возвращать ошибку, пока последовательность не будет перезапущена с помощью инструкции ALTER SEQUENCE.|  
|**last_used_value**|**sql_variant NULL**|Возвращает последнее значение, сформированное путем [Next Value For](../../t-sql/functions/next-value-for-transact-sql.md) функции. Применяется к SQL Server 2017 и более поздней версии.|  
  
## <a name="permissions"></a>Разрешения  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [CREATE SEQUENCE (Transact-SQL)](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE (Transact-SQL)](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE (Transact-SQL)](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR (Transact-SQL)](../../t-sql/functions/next-value-for-transact-sql.md)   
 [sp_sequence_get_range (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
