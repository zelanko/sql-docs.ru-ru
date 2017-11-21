---
title: "ALTER FULLTEXT CATALOG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FULLEXT_CATALOG_TSQL
- ALTER FULLEXT CATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- modifying full-text catalogs
- full-text catalogs [SQL Server], rebuilding
- accent sensitivity
- ALTER FULLTEXT CATALOG statement
- full-text catalogs [SQL Server], modifying
- full-text catalogs [SQL Server], reorganizing
ms.assetid: 31a47aaf-6c7f-48a4-a86a-d57aec66c9cb
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ffa9da60ccbf38265d46a6415fe461d492f8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-catalog-transact-sql"></a>ALTER FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет свойства полнотекстового каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER FULLTEXT CATALOG catalog_name   
{ REBUILD [ WITH ACCENT_SENSITIVITY = { ON | OFF } ]  
| REORGANIZE  
| AS DEFAULT   
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_каталога*  
 Задает имя изменяемого каталога. Если каталог с указанным именем не существует, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку и не выполняет операцию ALTER.  
  
 REBUILD  
 Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестроить весь каталог. Во время перестроения каталога существующий каталог удаляется, а на его месте создается новый каталог. Все таблицы, содержащие ссылки полнотекстового индексирования, сопоставляются с новым каталогом. Перестроение сбрасывает полнотекстовые метаданные в системных таблицах базы данных.  
  
 WITH ACCENT_SENSITIVITY = {ON|OFF}  
 Указывает, будет ли изменяемый каталог учитывать диакритические знаки при полнотекстовом индексировании и выполнении запросов.  
  
 Чтобы определить текущую настройку свойства учета диакритических знаков полнотекстового каталога, используйте функцию FULLTEXTCATALOGPROPERTY со **accentsensitivity** значение свойства от *имя_каталога*. Если функция возвращает «1», полнотекстовый каталог учитывает диакритические знаки; если функция возвращает «0», каталог не учитывает диакритические знаки.  
  
 По умолчанию учет диакритических знаков у каталога и у базы данных одинаков.  
  
 REORGANIZE  
 Сообщает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения *слияние в единый файл*, который включает в себя объединение небольших индексов, созданных в процессе индексирования, в один большой индекс. Слияние фрагментов полнотекстового индекса может повысить производительность и освободить ресурсы дисков и памяти. Если в полнотекстовом каталоге происходят частые изменения, следует периодически использовать эту команду для реорганизации каталога.  
  
 REORGANIZE также оптимизирует внутренние структуры индексов и каталогов.  
  
 Помните, что в зависимости от объема проиндексированных данных основное слияние может занять некоторое время. При слиянии больших объемов данных в единый файл может создаваться транзакция с большим временем выполнения, в результате чего усечение журнала транзакций по достижении контрольной точки будет отложено. В этом случае размер журнала транзакций в модели полного восстановления может значительно увеличиться. Перед реорганизацией большого полнотекстового индекса в базе данных, использующей модель полного восстановления, убедитесь, что в журнале транзакций достаточно свободного места для транзакций с большим временем выполнения. Дополнительные сведения см. в разделе [Управление размером файла журнала транзакций](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md).  
  
 AS DEFAULT  
 Указывает, что этот каталог является каталогом по умолчанию. При создании полнотекстовых индексов без указания конкретного каталога используется каталог по умолчанию. Если существует полнотекстовый каталог по умолчанию, то указание этого каталога AS DEFAULT переопределит существующее значение по умолчанию.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь разрешение ALTER для полнотекстового каталога или быть членом **db_owner**, **db_ddladmin** предопределенной роли базы данных или фиксированной серверной роли sysadmin.  
  
> [!NOTE]  
>  Для использования ALTER FULLTEXT CATALOG AS DEFAULT пользователь должен иметь разрешение ALTER для полнотекстового каталога и разрешение CREATE FULLTEXT CATALOG для базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующий пример изменяет свойство `accentsensitivity` полнотекстового каталога по умолчанию `ftCatalog`, который учитывает диакритические знаки.  
  
```  
--Change to accent insensitive  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog   
REBUILD WITH ACCENT_SENSITIVITY=OFF;  
GO  
-- Check Accentsensitivity  
SELECT FULLTEXTCATALOGPROPERTY('ftCatalog', 'accentsensitivity');  
GO  
--Returned 0, which means the catalog is not accent sensitive.  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [CREATE FULLTEXT CATALOG #40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  

