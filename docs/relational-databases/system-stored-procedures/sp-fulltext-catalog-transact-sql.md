---
title: sp_fulltext_catalog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a180f10f0b0ac4bb1836d529ac437d917b559e16
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820540"
---
# <a name="sp_fulltext_catalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает и удаляет полнотекстовый каталог, запускает и останавливает действие индексирования для каталога. Для каждой базы данных можно создать несколько полнотекстовых каталогов.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте инструкцию [CREATE FULLTEXT Catalog](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT Catalog](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)и [DROP FULLTEXT Catalog](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @ftcat = ] 'fulltext_catalog_name'`Имя полнотекстового каталога. Имена каталогов должны быть уникальными для каждой базы данных. *fulltext_catalog_name* имеет тип **sysname**.  
  
`[ @action = ] 'action'`Действие, которое необходимо выполнить. *Action* имеет тип **varchar (20)** и может принимать одно из следующих значений.  
  
> [!NOTE]  
>  Полнотекстовые каталоги можно создавать, удалять или изменять по мере необходимости. Однако не следует изменять схемы нескольких каталогов одновременно. Эти действия можно выполнить с помощью хранимой процедуры **sp_fulltext_table** , которая является рекомендуемым способом.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Создать**|Создает пустой полнотекстовый каталог в файловой системе и добавляет связанную строку в **таблицы sysfulltextcatalogs** с *fulltext_catalog_name* и *root_directory*, если она есть, значения. *fulltext_catalog_name* должны быть уникальными в пределах базы данных.|  
|**Тени**|Удаляет *fulltext_catalog_name* , удаляя его из файловой системы и удаляя связанную строку в **таблицы sysfulltextcatalogs**. Действие не будет выполнено, если каталог содержит индексы для одной или нескольких таблиц. **sp_fulltext_table** для удаления таблиц из каталога необходимо выполнить "*table_name*", "Drop".<br /><br /> Если каталог не существует, появится сообщение об ошибке.|  
|**start_incremental**|Запускает добавочное заполнение для *fulltext_catalog_name*. Если каталог не существует, появится сообщение об ошибке. Если заполнение полнотекстового индекса уже выполняется, то появляется предупреждение, а заполнение отменяется. При добавочном заполнении только измененные строки извлекаются для полнотекстового индексирования. при условии, что в таблице имеется столбец **timestamp** , в котором выполняется полнотекстовое индексирование.|  
|**start_full**|Запускает полное заполнение для *fulltext_catalog_name*. Для полнотекстового индексирования извлекаются все строки всех таблиц, связанных с полнотекстовым каталогом, даже если они уже проиндексированы.|  
|**Остановить**|Останавливает заполнение индекса для *fulltext_catalog_name*. Если каталог не существует, появится сообщение об ошибке. Если заполнение уже остановлено, предупреждение не отображается.|  
|**Перестроение**|Перестраивает *fulltext_catalog_name*. Во время перестроения каталога существующий каталог удаляется, а на его месте создается новый каталог. Все таблицы, содержащие ссылки полнотекстового индексирования, сопоставляются с новым каталогом. Перестроение сбрасывает полнотекстовые метаданные в системных таблицах базы данных.<br /><br /> Если отслеживание изменений отключено, то перестроение не приводит к повторному заполнению вновь созданного полнотекстового каталога. В этом случае для повторного заполнения выполните **sp_fulltext_catalog** с действием **start_full** или **start_incremental** .|  
  
`[ @path = ] 'root_directory'`Корневой каталог (а не полный физический путь) для действия **создания** . *root_directory* имеет тип **nvarchar (100)** и имеет значение по умолчанию NULL, которое указывает на использование расположения по умолчанию, указанного при установке. Это подкаталог FTDATA в каталоге MSSQL; Например, C:\Program Files\Microsoft SQL Server\MSSQL13. мссклсервер\мсскл\фтдата. Указанный каталог должен находиться на локальном диске, его имя не может состоять только из одной буквы диска, и путь к этому каталогу не может быть относительным. Сетевые, съемные, гибкие диски и UNC-пути не поддерживаются. Полнотекстовые каталоги можно создавать на локальных жестких дисках, связанных с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ** \@ путь** допустим только при создании *действия* . **create** Для действий, отличных от **CREATE** (**останавливаться**, **REBUILD**и т. д.), ** \@ путь** должен иметь значение null или быть пропущен.  
  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является виртуальным сервером кластера, то указанный каталог должен находиться на общем диске с ресурсами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если @path параметр не указан, расположение каталога каталога по умолчанию находится на общем диске в каталоге, указанном при установке виртуального сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Действие **start_full** используется для создания полного моментального снимка полнотекстовых данных в *fulltext_catalog_name*. Действие **start_incremental** используется для повторной индексации только измененных строк в базе данных. Добавочное заполнение можно применять только в том случае, если в таблице есть столбец типа **timestamp**. Если таблица в полнотекстовом каталоге не содержит столбец типа **timestamp**, то таблица будет полностью заполнена.  
  
 Полнотекстовый каталог и данные индекса хранятся в файлах в отдельной папке. Каталог полнотекстового каталога создается в виде вложенного каталога каталога, указанного в параметре ** \@ path** , или в каталоге полнотекстового каталога сервера по умолчанию, если ** \@ путь** не указан. Имя папки полнотекстового каталога формируется таким образом, чтобы оно было уникальным в пределах сервера. Следовательно, для всех папок полнотекстовых каталогов сервера можно использовать общий путь.  
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть членом роли **db_owner** . В зависимости от запрошенного действия вызывающему объекту не следует отклонять разрешения ALTER или CONTROL (которые **db_owner** имеют) в целевом полнотекстовом каталоге.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-full-text-catalog"></a>A. Создание полнотекстового каталога  
 В этом примере создается пустой полнотекстовый каталог **Cat_Desc**в базе данных **AdventureWorks2012** .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>Б. Перестроение полнотекстового каталога  
 В этом примере перестраивается существующий полнотекстовый каталог **Cat_Desc**в базе данных **AdventureWorks2012** .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>В. Запуск заполнения полнотекстового каталога  
 В этом примере начинается полное заполнение каталога **Cat_Desc** .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>Г. Остановка заполнения полнотекстового каталога  
 В этом примере прекращается заполнение каталога **Cat_Desc** .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>Д. Удаление полнотекстового каталога  
 В этом примере удаляется каталог **Cat_Desc** .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
