---
title: IHarticles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHarticles
- IHarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHarticles system table
ms.assetid: 773ef9b7-c993-4629-9516-70c47b9dcf65
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45278a6d9501b75b624e11bbeb11d24d10e482c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056210"
---
# <a name="iharticles-transact-sql"></a>IHarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHarticles** системная таблица содержит по одной строке для каждой статьи, реплицируемой с отличным от SQL Server издателя с помощью текущего распространителя. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Столбец идентификаторов, в котором хранится уникальный идентификатор статьи.|  
|**name**|**sysname**|Имя, ассоциированное со статьей, уникальное внутри публикации.|  
|**publication_id**|**smallint**|Идентификатор публикации, к которой принадлежит статья.|  
|**table_id**|**int**|Идентификатор таблицы, публикуемой из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md).|  
|**publisher_id**|**smallint**|Идентификатор издателя, отличные от SQL Server.|  
|**creation_script**|**nvarchar(255)**|Скрипт схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном удалении в статьях таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**фильтр**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**filter_clause**|**ntext**|Предложение статьи WHERE, используемое для горизонтальной фильтрации и написанное на стандартном языке Transact-SQL, который может интерпретироваться издателем, не являющимся SQL Server.|  
|**ins_cmd**|**nvarchar(255)**|Тип команды репликации, используемый при репликационной вставке в статьи таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**pre_creation_cmd**|**tinyint**|Команда, которую необходимо выполнить перед применением исходного моментального снимка, если объект с тем же именем уже существует на подписчике.<br /><br /> **0** = none — команда не выполняется.<br /><br /> **1** = DROP — удалить целевую таблицу.<br /><br /> **2** = DELETE — удалить данные из целевой таблицы.<br /><br /> **3** = TRUNCATE — выполнить усечение целевой таблицы.|  
|**status**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом операции побитового логического ИЛИ над одним или несколькими из следующих значений:<br /><br /> **0** = нет дополнительных свойств.<br /><br /> **1** = активно.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> Например, для активной статьи, в которой используются параметризованные инструкции, значение данного столбца должно быть равно 17. Значение 0 указывает, что статья неактивна и никакие дополнительные свойства не определены.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.|  
|**upd_cmd**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном обновлении статей таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**schema_option**|**binary(8)**|Битовая карта параметра формирования схемы для конкретной статьи, которая может быть результатом операции побитового логического ИЛИ над одним или несколькими из следующих значений:<br /><br /> **0x00** = запретить использование сценариев агента моментальных снимков и использует предоставленный CreationScript.<br /><br /> **0x01** = формировать инструкции создания объектов (CREATE TABLE, CREATE PROCEDURE и т. д.).<br /><br /> **0x10** = формировать соответствующий кластеризованный индекс.<br /><br /> **0x40** = формировать соответствующие некластеризованные индексы.<br /><br /> **0x80** = включить для первичных ключей объявления ссылочной целостности.<br /><br /> **0x1000** = реплицирует параметры сортировки на уровне столбцов. Примечание. Этот параметр имеет значение по умолчанию для издателей Oracle для включения сравнений с учетом регистра.<br /><br /> **0x4000** = реплицировать уникальные ключи, если они определены для статьи таблицы.<br /><br /> **0x8000** = реплицировать первичный ключ и уникальные ключи в таблице статьи как ограничения при помощи инструкции ALTER TABLE.|  
|**dest_owner**|**sysname**|Владелец таблицы в целевой базе данных.|  
|**dest_table**|**sysname**|Имя целевой таблицы.|  
|**tablespace_name**|**nvarchar(255)**|Определяет табличное пространство, используемое регистрирующей таблицей для статьи.|  
|**objID**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**sync_objid**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**description**|**nvarchar(255)**|Описание статьи.|  
|**publisher_status**|**int**|Указывает, определен ли представление, определяющее публикуемую статью, вызвав [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md).<br /><br /> **0** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) был вызван.<br /><br /> **1** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) не был вызван.|  
|**article_view_owner**|**nvarchar(255)**|Владелец объекта синхронизации на издателе, используемого агентом чтения журнала.|  
|**article_view**|**nvarchar(255)**|Объект синхронизации на издателе, используемый агентом чтения журнала.|  
|**ins_scripting_proc**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**del_scripting_proc**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**upd_scripting_proc**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**custom_script**|**int**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**fire_triggers_on_snapshot**|**bit**|Этот столбец не используется и включен только для того, чтобы сделать [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление **IHarticles** таблицы, совместимый с [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) представление, используемое для статьи (SQL Server [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**instance_id**|**int**|Определяет текущий экземпляр журнала статьи для опубликованной таблицы.|  
|**use_default_datatypes**|**bit**|Указывает, использует ли статья сопоставления типов данных по умолчанию; значение **1** указывает, что используются сопоставления типов данных по умолчанию.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)  
  
  
