---
title: "sys.partitions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 658d0d22bf2dc757854626f792cc49429ab98916
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Содержит одну строку для каждой секции всех таблиц и большинства типов индексов базы данных. Специальные типы индекса, такие как полнотекстовый, пространственный и XML, не включены в это представление. Считается, что все таблицы и индексы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержат как минимум одну секцию, даже если они явно не секционированы.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|object_id|**int**|Указывает идентификатор объекта, которому принадлежит данная секция. Каждая таблица или представление содержит как минимум одну секцию.|  
|index_id|**int**|Указывает идентификатор индекса в пределах объекта, которому принадлежит данная секция.<br /><br /> 0 = куча<br />1 = кластеризованный индекс<br />2 или больше = некластеризованный индекс|  
|partition_number|**int**|Является номером секции (начиная с 1) во владеющем ей индексе или куче. Для несекционированных таблиц и индексов значение этого столбца равно 1.|  
|hobt_id|**bigint**|Указывает идентификатор кучи данных или сбалансированного дерева, содержащего строки данной секции.|  
|rows|**bigint**|Указывает приблизительное количество строк в данной секции.|  
|filestream_filegroup_id|**smallint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает ID для файловой группы FILESTREAM, хранимой в этой секции.|  
|data_compression|**tinyint**|Указывает состояние сжатия для каждой секции.<br /><br /> 0 = нет <br />1 = ROW <br />2 = PAGE <br />3 = COLUMNSTORE: **применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />4 = COLUMNSTORE_ARCHIVE: **применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> **Примечание:** полнотекстовые индексы будут сжаты в любом выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|data_compression_desc|**nvarchar(60)**|Указывает состояние сжатия для каждой секции. Возможные значения для таблиц rowstore: NONE, ROW и PAGE. Возможные значения для таблиц columnstore: COLUMNSTORE и COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
