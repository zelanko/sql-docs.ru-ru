---
title: sys. data_spaces (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- data_spaces
- sys.data_spaces_TSQL
- sys.data_spaces
- data_spaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.data_spaces catalog view
ms.assetid: f39d55fe-2c0f-472d-a77f-cebc6fea95b5
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 203c16e818d8a53cd025065d9c49ef8c5aeebcfd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73983192"
---
# <a name="sysdata_spaces-transact-sql"></a>sys.data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого пространства данных. Это может быть файловая группа, схема секционирования или файловая группа данных FILESTREAM.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|name|**имеет sysname**|Имя пространства данных, уникальное внутри базы данных.|  
|data_space_id|**int**|Номер идентификатора пространства данных, уникальный внутри базы данных.|  
|type|**char (2)**|Тип пространства данных:<br /><br /> FG = файловая группа<br /><br /> FD = файловая группа данных FILESTREAM<br /><br /> FX = файловая группа таблиц, оптимизированных для памяти<br /><br /> **Область применения**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более поздних версий.<br /><br /> PS = схема секционирования|  
|type_desc|**nvarchar (60)**|Описание типа пространства данных:<br /><br /> FILESTREAM_DATA_FILEGROUP<br /><br /> MEMORY_OPTIMIZED_DATA_FILEGROUP<br /><br /> **Область применения**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более поздних версий.<br /><br /> PARTITION_SCHEME<br /><br /> ROWS_FILEGROUP|  
|is_default|**bit**|1 = пространство данных по умолчанию. Это пространство данных используется по умолчанию, если файловая группа или схема секционирования не задана в инструкции CREATE TABLE или CREATE INDEX.<br /><br /> 0 = не является пространством данных по умолчанию.|  
|is_system|**bit**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> 1 = пространство данных используется для фрагментов полнотекстового индекса.<br /><br /> 0 = пространство данных не используется для фрагментов полнотекстового индекса.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Пространства данных &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. databases &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. destination_data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys. FILEGROUP &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys. partition_schemes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
