---
title: sp_fulltext_catalog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7bd63fff2c2c395648a1ac8a61903db007cafc96
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559774"
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает и удаляет полнотекстовый каталог, запускает и останавливает действие индексирования для каталога. Для каждой базы данных можно создать несколько полнотекстовых каталогов.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md), и [DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@ftcat=**] **'***fulltext_catalog_name***'**  
 Имя полнотекстового каталога. Имена каталогов должны быть уникальными для каждой базы данных. *fulltext_catalog_name* — **sysname**.  
  
 [  **@action=**] **"***действие***"**  
 Действие, которое должно быть выполнено. *Действие* — **varchar(20)**, и может принимать одно из следующих значений.  
  
> [!NOTE]  
>  Полнотекстовые каталоги можно создавать, удалять или изменять по мере необходимости. Однако не следует изменять схемы нескольких каталогов одновременно. Эти действия можно выполнить с помощью **sp_fulltext_table** хранимые процедуры, которая является рекомендуемым способом.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Создание**|Создает новый пустой полнотекстовый каталог в файловой системе и добавляет строку в **sysfulltextcatalogs** с *fulltext_catalog_name* и *root_directory*, Если он присутствует, значения. *fulltext_catalog_name* должно быть уникальным в базе данных.|  
|**Drop**|Удаляет *fulltext_catalog_name* , удалив его из файловой системы и строку в **sysfulltextcatalogs**. Действие не будет выполнено, если каталог содержит индексы для одной или нескольких таблиц. **sp_fulltext_table** "*table_name*", «drop» должны выполняться для удаления таблиц из каталога.<br /><br /> Если каталог не существует, появится сообщение об ошибке.|  
|**start_incremental**|Запускает добавочное заполнение для *fulltext_catalog_name*. Если каталог не существует, появится сообщение об ошибке. Если заполнение полнотекстового индекса уже выполняется, то появляется предупреждение, а заполнение отменяется. При добавочном заполнении только измененные строки извлекаются для полнотекстового индексирования, условии, что **timestamp** столбцы, присутствующие в таблице полнотекстового индексирования.|  
|**start_full**|Запускает полное заполнение для *fulltext_catalog_name*. Для полнотекстового индексирования извлекаются все строки всех таблиц, связанных с полнотекстовым каталогом, даже если они уже проиндексированы.|  
|**Остановить**|Останавливает заполнение индекса для *fulltext_catalog_name*. Если каталог не существует, появится сообщение об ошибке. Если заполнение уже остановлено, предупреждение не отображается.|  
|**Rebuild**|Перестраивает *fulltext_catalog_name*. Во время перестроения каталога существующий каталог удаляется, а на его месте создается новый каталог. Все таблицы, содержащие ссылки полнотекстового индексирования, сопоставляются с новым каталогом. Перестроение сбрасывает полнотекстовые метаданные в системных таблицах базы данных.<br /><br /> Если отслеживание изменений отключено, то перестроение не приводит к повторному заполнению вновь созданного полнотекстового каталога. В этом случае для повторного заполнения выполните **sp_fulltext_catalog** с **start_full** или **start_incremental** действие.|  
  
 [  **@path=**] **"***root_directory***"**  
 Является корневым каталогом (не полный физический путь) для **создать** действие. *root_directory* — **nvarchar(100)** и имеет значение по умолчанию NULL, которое указывает на использование расположения по умолчанию, заданное при установке. Это подкаталог Ftdata в каталоге Mssql. Например, C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\FTData. Указанный каталог должен находиться на локальном диске, его имя не может состоять только из одной буквы диска, и путь к этому каталогу не может быть относительным. Сетевые, съемные, гибкие диски и UNC-пути не поддерживаются. Полнотекстовые каталоги можно создавать на локальных жестких дисках, связанных с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **@path** доступен, только если *действие* — **создание**. Для действий, отличных от **создать** (**остановить**, **Перестроить**, и так далее), **@path** должен иметь значение NULL или не указано.  
  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является виртуальным сервером кластера, то указанный каталог должен находиться на общем диске с ресурсами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если @path не указан, по умолчанию каталог находится на общем диске в каталоге, который был указан при установке виртуального сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **Start_full** действие используется для создания моментального снимка данных полнотекстового поиска в *fulltext_catalog_name*. **Start_incremental** действие используется для повторного индексирования измененных строк в базе данных. Добавочное заполнение может применяться только в том случае, если в таблице есть столбец типа **timestamp**. Если таблицы в полнотекстовый каталог не содержит столбец типа **timestamp**, то выполняется полное заполнение.  
  
 Полнотекстовый каталог и данные индекса хранятся в файлах в отдельной папке. Полнотекстовый каталог создается как вложенный каталог каталога, заданного в **@path** или в каталоге полнотекстовый каталог по умолчанию сервера Если **@path** не указан. Имя папки полнотекстового каталога формируется таким образом, чтобы оно было уникальным в пределах сервера. Следовательно, для всех папок полнотекстовых каталогов сервера можно использовать общий путь.  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть членом **db_owner** роли. В зависимости от запрашиваемого действия, вызывающего объекта не должны быть запрещены разрешения ALTER или CONTROL (который **db_owner** имеет) на целевой каталог полнотекстового поиска.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-full-text-catalog"></a>A. Создание полнотекстового каталога  
 В этом примере создается пустой полнотекстовый каталог **Cat_Desc**в **AdventureWorks2012** базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>Б. Перестроение полнотекстового каталога  
 В этом примере перестраивается существующий полнотекстовый каталог, **Cat_Desc**в **AdventureWorks2012** базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>В. Запуск заполнения полнотекстового каталога  
 Пример запуска полного заполнения **Cat_Desc** каталога.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>Г. Остановка заполнения полнотекстового каталога  
 В этом примере останавливает заполнение **Cat_Desc** каталога.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>Д. Удаление полнотекстового каталога  
 В этом примере удаляется **Cat_Desc** каталога.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [FULLTEXTCATALOGPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
