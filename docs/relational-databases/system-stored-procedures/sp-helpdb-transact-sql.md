---
title: sp_helpdb (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 81ecc4cba94db62ff6f7fb6960d989a205ca8eae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сообщает информацию об указанной базе данных или всех базах данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbname=** ] **"***имя***"**  
 Имя базы данных, для которой выводятся сведения. *имя* — **sysname**, не имеет значения по умолчанию. Если *имя* не указан, **sp_helpdb** сообщает обо всех базах данных в **sys.databases** представления каталога.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных.|  
|**db_size**|**nvarchar(13)**|Общий размер базы данных.|  
|**Владелец**|**sysname**|Владелец базы данных, таких как **sa**.|  
|**dbid**|**smallint**|Идентификатор базы данных.|  
|**Создан**|**nvarchar(11)**|Дата создания базы данных.|  
|**status**|**nvarchar(600)**|Разделенный запятыми список значений параметров базы данных, которые в данный момент установлены для базы данных.<br /><br /> Перечислены только включенные параметры с логическими значениями. Нелогические параметры перечислены с соответствующими значениями в виде *option_name*=*значение*.<br /><br /> Дополнительные сведения см. в статье [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).|  
|**compatibility_level**|**tinyint**|Уровень совместимости базы данных: 60, 65, 70, 80 или 90.|  
  
 Если *имя* указан, существует дополнительный результирующий набор, который показывает распределение файлов для указанной базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nchar(128)**|Логическое имя файла.|  
|**fileid**|**smallint**|Идентификатор файла.|  
|**Имя файла**|**nchar(260)**|Имя файла в операционной системе (физическое имя файла).|  
|**filegroup**|**nvarchar(128)**|Файловая группа, к которой принадлежит файл.<br /><br /> NULL = файл является файлом журнала. Такой файл никогда не является частью файловой группы.|  
|**size**|**nvarchar(18)**|Размер файла в мегабайтах.|  
|**параметр MaxSize**|**nvarchar(18)**|Определяет максимальный размер, до которого может вырасти файл. Значение UNLIMITED в этом поле означает, что файл может расти, пока диск не будет заполнен.|  
|**Увеличение размера**|**nvarchar(18)**|Значение прироста размера файла. Размер пространства, добавляемого в файл каждый раз, когда требуется новое пространство.|  
|**Использование**|**varchar(9)**|Применение файла. Для файла данных, значение равно **«данные»** и файла журнала, оно **только для журнала**.|  
  
## <a name="remarks"></a>Замечания  
 **Состояние** столбец результирующего набора отчетов, какие параметры заданы в значение ON в базе данных. Все параметры базы данных не сообщает о **состояние** столбца. Чтобы просмотреть полный список текущих параметров базы данных, используйте **sys.databases** представления каталога.  
  
## <a name="permissions"></a>Разрешения  
 При указании отдельной базы данных, членство в **открытый** требуется роль базы данных. Если база данных не указан, членство в **открытый** роль в **master** необходима база данных.  
  
 Если база данных недоступна, **sp_helpdb** отображает сведения об ошибке номер 15622 и столько о базе данных, как.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-information-about-a-single-database"></a>A. Информация, возвращаемая о единственной базе данных  
 В следующем примере отображается информация о базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>Б. Информация, возвращаемая обо всех базах данных  
 В следующем примере отображается информация обо всех базах данных, работающих на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
