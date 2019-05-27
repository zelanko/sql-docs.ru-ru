---
title: Устаревшие функции полнотекстового поиска в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [full-text search]
- full-text search [SQL Server], deprecated features
- full-text queries [SQL Server], proximity
ms.assetid: ab0d799c-ba79-4459-837b-c4862730dafd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a49d7db68fe32d9794e89db66020d7f90555508
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011403"
---
# <a name="deprecated-full-text-search-features-in-sql-server-2014"></a>Устаревшие функции полнотекстового поиска в SQL Server 2014
  В этом разделе описаны устаревшие функции полнотекстового поиска, по-прежнему доступные в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
 Наблюдать за использованием нерекомендуемых функций можно с помощью событий трассировки и объекта производительности **SQL Server:Deprecated Features** . Дополнительные сведения см. в разделе [Использование объектов SQL Server](../performance-monitor/use-sql-server-objects.md).  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Функции, не поддерживаемые в следующей версии SQL Server  
 Следующие возможности полнотекстового поиска не будут поддерживаться в следующем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Устаревшая функция|Замена|Имя функции|Идентификатор функции|  
|------------------------|-----------------|------------------|----------------|  
|Свойство FULLTEXTCATALOGPROPERTY: LogSize|Нет.|FULLTEXTCATALOGPROPERTY **('LogSize')**|211|  
|Свойство FULLTEXTSERVICEPROPERTY:<br /><br /> ConnectTimeout<br /><br /> DataTimeout|Нет.|FULLTEXTSERVICEPROPERTY **('ConnectTimeout')**<br /><br /> FULLTEXTSERVICEPROPERTY **('DataTimeout'**)|210<br /><br /> 209|  
|sp_fulltext_catalog|CREATE FULL CATALOG<br /><br /> ALTER FULLTEXT CATALOG<br /><br /> DROP FULLTEXT CATALOG|sp_fulltext_catalog|84|  
|sp_fulltext_column<br /><br /> sp_fulltext_database, хранимая процедура<br /><br /> sp_fulltext_table|CREATE FULL INDEX<br /><br /> ALTER FULLTEXT INDEX<br /><br /> DROP FULLTEXT INDEX|sp_fulltext_column<br /><br /> sp_fulltext_database, хранимая процедура<br /><br /> sp_fulltext_table|86<br /><br /> 87<br /><br /> 85|  
|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_tables<br /><br /> sp_help_fulltext_tables_cursor|sys.fulltext_catalogs<br /><br /> sys.fulltext_index_columns<br /><br /> sys.fulltext_indexes|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_table<br /><br /> sp_help_fulltext_tables_cursor|88<br /><br /> 203<br /><br /> 90<br /><br /> 92<br /><br /> 93<br /><br /> 91<br /><br /> 89|  
|значения действий хранимой процедуры sp_fulltext_service: clean_up, connect_timeout, and data_timeout возвращают нуль|None|sp_fulltext_service @action=clean_up<br /><br /> sp_fulltext_service @action=connect_timeout<br /><br /> sp_fulltext_service @action=data_timeout|116<br /><br /> 117<br /><br /> 118|  
|Столбцы представления sys.dm_fts_active_catalogs:<br /><br /> is_paused<br /><br /> previous_status<br /><br /> previous_status_description<br /><br /> row_count_in_thousands<br /><br /> status<br /><br /> status_description<br /><br /> worker_count|Нет.|dm_fts_active_catalogs.is_paused<br /><br /> dm_fts_active_catalogs.previous_status<br /><br /> dm_fts_active_catalogs.previous_status_description<br /><br /> dm_fts_active_catalogs.row_count_in_thousands<br /><br /> dm_fts_active_catalogs.status<br /><br /> dm_fts_active_catalogs.status_description<br /><br /> dm_fts_active_catalogs.worker_count|218<br /><br /> 221<br /><br /> 222<br /><br /> 224<br /><br /> 219<br /><br /> 220<br /><br /> 223|  
|Столбец представления sys.dm_fts_memory_buffers:<br /><br /> row_count|Нет.|dm_fts_memory_buffers.row_count|225|  
|Столбцы представления sys.fulltext_catalogs:<br /><br /> path<br /><br /> data_space_id<br /><br /> file_id|Нет.|fulltext_catalogs.path<br /><br /> fulltext_catalogs.data_space_id<br /><br /> fulltext_catalogs.file_id|215<br /><br /> 216<br /><br /> 217|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Функции, не поддерживаемые в будущей версии SQL Server  
 Поддержка приведенных ниже функций полнотекстового поиска в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]будет сохранена, однако они будут удалены в более поздних версиях. (с какой именно версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока не определено).  
  
 Значение **Имя функции** фигурирует в событиях трассировки как ObjectName, а в счетчиках производительности и административном представлении sys.dm_os_performance_counters как "instance name". Значению **Идентификатор функции** в событиях трассировки соответствует ObjectId.  
  
|Устаревшая функция|Замена|Имя функции|Идентификатор функции|  
|------------------------|-----------------|------------------|----------------|  
|инструкции CONTAINS и CONTAINSTABLE, универсальный оператор NEAR:<br /><br /> {<simple_term> &#124; <prefix_term>}<br /><br /> {<br /><br /> { { NEAR &#124; ~ }    {<simple_term> &#124; <prefix_term>} } [...*n*]<br /><br /> }|Пользовательский оператор NEAR:<br /><br /> NEAR(<br /><br /> {   {<simple_term> &#124; <prefix_term>} [ ,...*n* ]<br /><br /> &#124; ( {<simple_term> &#124; <prefix_term>} [,...*n*] )<br /><br /> [,\<расстояние > [,\<порядок >]]<br /><br /> }<br /><br /> )<br /><br /> \<distance> ::= {*integer* &#124; **MAX**}<br /><br /> \<order> ::= {TRUE &#124; **FALSE**}|FULLTEXT_OLD_NEAR_SYNTAX|247|  
|Параметр CREATE FULLTEXT CATALOG:<br /><br /> IN PATH '*rootpath*'<br /><br /> ON FILEGROUP *filegroup*|Нет.|CREATE FULLTEXT CATLOG IN PATH<br /><br /> Нет.*|237<br /><br /> Нет.<sup>*</sup>|  
|Свойство DATABASEPROPERTYEX: IsFullTextEnabled|Нет.|DATABASEPROPERTYEX **('IsFullTextEnabled')**|202|  
|Параметр sp_detach_db:<br /><br /> [ @keepfulltextindexfile = ] '*KeepFulltextIndexFile*'|Нет.|sp_detach_db @keepfulltextindexfile|226|  
|значение действий хранимой процедуры sp_fulltext_service: resource_usage не имеет функции.|None|sp_fulltext_service @action=resource_usage|200|  
  
 \*Объект **SQL Server:Deprecated Features** не отслеживает появление инструкций CREATE FULLTEXT CATLOG ON FILEGROUP *filegroup*.  
  
## <a name="see-also"></a>См. также  
 [SQL Server, объект Deprecated Features](../performance-monitor/sql-server-deprecated-features-object.md)   
 [Критические изменения в компонент Full-Text Search](../../database-engine/breaking-changes-to-full-text-search.md)   
 [Нерекомендуемые функции ядра СУБД в SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
