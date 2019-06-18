---
title: Инструкции DDL, функции, хранимые процедуры и представления для семантического поиска | Документация Майкрософт
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 3d1ca2fc989fb2447b0d81e43f4da99a9313ab5c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62716151"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>Инструкции семантического поиска DDL, функции, хранимые процедуры и представления
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Содержит список инструкций Transact-SQL и объектов базы данных, которые поддерживают статистический семантический поиск в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список инструкций и объектов базы данных, которые поддерживают полнотекстовый поиск, см. в статье [Инструкции полнотекстового поиска DDL, функции, хранимые процедуры и представления](../../relational-databases/search/full-text-search-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="ddl"></a> Инструкции языка описания данных DDL  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)|[Включение семантического поиска на таблицы и столбцы](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)|[Включение семантического поиска по таблицам и столбцам](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> Системные функции  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[semantickeyphrasetable (Transact-SQL)](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)|[Поиск ключевых фраз в документах с помощью семантического поиска](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)|[Поиск похожих и связанных документов с помощью семантического поиска](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable (Transact-SQL)](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)|[Поиск похожих и связанных документов с помощью семантического поиска](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> Системные функции метаданных  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[COLUMNPROPERTY (Transact-SQL)](../../t-sql/functions/columnproperty-transact-sql.md)|[Включение семантического поиска по таблицам и столбцам](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)|[Включение семантического поиска на таблицы и столбцы](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|[Управление и наблюдение за семантическим поиском](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY (Transact-SQL)](../../t-sql/functions/indexproperty-transact-sql.md)|[Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX (Transact-SQL)](../../t-sql/functions/objectpropertyex-transact-sql.md)|[Включение семантического поиска по таблицам и столбцам](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)|[Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> Системные хранимые процедуры  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md)|[Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md)|[Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> Представления каталога  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|[Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)|[Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)|[Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> Динамические административные представления  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)|[Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|[Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)|[Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>См. также:  
 [Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
