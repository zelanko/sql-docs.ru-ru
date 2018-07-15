---
title: Инструкции DDL, функции, хранимые процедуры и представления для семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0632ec8d1222c1bdbda816052d5cfef7ff63ef16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208674"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>Инструкции семантического поиска DDL, функции, хранимые процедуры и представления
  Содержит список инструкций Transact-SQL и объектов базы данных, которые поддерживают статистический семантический поиск в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список инструкций и объектов базы данных, которые поддерживают полнотекстовый поиск, см. в статье [Инструкции полнотекстового поиска DDL, функции, хранимые процедуры и представления](../views/views.md).  
  
##  <a name="ddl"></a> Инструкции языка описания данных (DDL) Transact-SQL  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[Включение семантического поиска по таблицам и столбцам](enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[Включение семантического поиска по таблицам и столбцам](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> Системные функции  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[Поиск ключевых фраз в документах с помощью семантического поиска](find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[Поиск похожих и связанных документов с помощью семантического поиска](find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[Поиск похожих и связанных документов с помощью семантического поиска](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> Системные функции метаданных  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[COLUMNPROPERTY (Transact-SQL)](/sql/t-sql/functions/columnproperty-transact-sql)|[Включение семантического поиска по таблицам и столбцам](enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX (Transact-SQL)](/sql/t-sql/functions/databasepropertyex-transact-sql)|[Включение семантического поиска на таблицы и столбцы](enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY (Transact-SQL)](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[Управление и наблюдение за семантическим поиском](manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY (Transact-SQL)](/sql/t-sql/functions/indexproperty-transact-sql)|[Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX (Transact-SQL)](/sql/t-sql/functions/objectproperty-transact-sql)|[Включение семантического поиска по таблицам и столбцам](enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)|[Установка и настройка семантического поиска](install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> Системные хранимые процедуры  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[Установка и настройка семантического поиска](install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[Установка и настройка семантического поиска](install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> Системные представления — представления каталога  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sys.fulltext_index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[Установка и настройка семантического поиска](install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[Установка и настройка семантического поиска](install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> Системные представления — динамические административные представления  
  
|Объект|Дополнительные сведения|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>См. также  
 [Управление семантическим поиском и наблюдение за ним](manage-and-monitor-semantic-search.md)  
  
  
