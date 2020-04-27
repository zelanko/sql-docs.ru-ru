---
title: sp_helpdb (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7acc14d3950e0e2d1004727b2efbffd2e4963a2b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67903022"
---
# <a name="sp_helpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сообщает информацию об указанной базе данных или всех базах данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'name'`Имя базы данных, для которой сообщается информация. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию. Если параметр *Name* не указан, **sp_helpdb** отчеты по всем базам данных в представлении каталога **sys. databases** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|имя базы данных.|  
|**db_size**|**nvarchar (13)**|Общий размер базы данных.|  
|**владельцев**|**sysname**|Владелец базы данных, например **SA**.|  
|**DBID**|**smallint**|Идентификатор базы данных.|  
|**created**|**nvarchar(11)**|Дата создания базы данных.|  
|**status**|**nvarchar (600)**|Разделенный запятыми список значений параметров базы данных, которые в данный момент установлены для базы данных.<br /><br /> Перечислены только включенные параметры с логическими значениями. Параметры, не являющиеся логическими, перечислены с соответствующими значениями в виде *option_name*=*значения*.<br /><br /> Дополнительные сведения см. в разделе [ALTER database &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).|  
|**compatibility_level**|**tinyint**|Уровень совместимости базы данных: 60, 65, 70, 80 или 90.|  
  
 Если указано *имя* , то существует дополнительный результирующий набор, который показывает размещение файлов для указанной базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nchar (128)**|Логическое имя файла.|  
|**ИД**|**smallint**|Идентификатор файла.|  
|**файлов**|**nchar (260)**|Имя файла в операционной системе (физическое имя файла).|  
|**файловой группы**|**nvarchar(128)**|Файловая группа, к которой принадлежит файл.<br /><br /> NULL = файл является файлом журнала. Такой файл никогда не является частью файловой группы.|  
|**size**|**nvarchar (18)**|Размер файла в мегабайтах.|  
|**MAXSIZE**|**nvarchar (18)**|Определяет максимальный размер, до которого может вырасти файл. Значение UNLIMITED в этом поле означает, что файл может расти, пока диск не будет заполнен.|  
|**growth**|**nvarchar (18)**|Значение прироста размера файла. Размер пространства, добавляемого в файл каждый раз, когда требуется новое пространство.|  
|**Загрузка**|**varchar (9)**|Применение файла. Для файла данных значением является **"только данные"** , а для файла журнала — **"только журнал"**.|  
  
## <a name="remarks"></a>Remarks  
 Столбец **Status** в результирующем наборе сообщает, какие параметры были установлены в значение ON в базе данных. Столбец **Status** не сообщает обо всех параметрах базы данных. Чтобы просмотреть полный список текущих настроек параметров базы данных, используйте представление каталога **sys. databases** .  
  
## <a name="permissions"></a>Разрешения  
 Если указана единственная база данных, необходимо членство в роли **Public** в базе данных. Если база данных не указана, требуется членство в роли **Public** в базе данных **master** .  
  
 Если доступ к базе данных невозможен, **sp_helpdb** отображает сообщение об ошибке 15622 и как можно больше сведений о базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-information-about-a-single-database"></a>A. Информация, возвращаемая о единственной базе данных  
 В следующем примере отображается информация о базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>Б) Информация, возвращаемая обо всех базах данных  
 В следующем примере отображается информация обо всех базах данных, работающих на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. FILEGROUP &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys. master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
