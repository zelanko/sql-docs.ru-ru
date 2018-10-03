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
manager: craigg
ms.openlocfilehash: c6d514adfed27693456338ece6fa58638e319475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629812"
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
|**значение db_size**|**nvarchar(13)**|Общий размер базы данных.|  
|**Владелец**|**sysname**|Владелец базы данных, таких как **sa**.|  
|**dbid**|**smallint**|Идентификатор базы данных.|  
|**Создан**|**nvarchar(11)**|Дата создания базы данных.|  
|**status**|**nvarchar(600)**|Разделенный запятыми список значений параметров базы данных, которые в данный момент установлены для базы данных.<br /><br /> Перечислены только включенные параметры с логическими значениями. Не являющиеся логическими параметры перечислены с соответствующими значениями в виде *option_name*=*значение*.<br /><br /> Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).|  
|**compatibility_level**|**tinyint**|Уровень совместимости базы данных: 60, 65, 70, 80 и 90.|  
  
 Если *имя* указано, есть дополнительный результирующий набор, который показывает распределение файлов для указанной базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nchar(128)**|Логическое имя файла.|  
|**fileid**|**smallint**|Идентификатор файла.|  
|**Имя файла**|**nchar(260)**|Имя файла в операционной системе (физическое имя файла).|  
|**filegroup**|**nvarchar(128)**|Файловая группа, к которой принадлежит файл.<br /><br /> NULL = файл является файлом журнала. Такой файл никогда не является частью файловой группы.|  
|**size**|**nvarchar(18)**|Размер файла в мегабайтах.|  
|**параметр MaxSize**|**nvarchar(18)**|Определяет максимальный размер, до которого может вырасти файл. Значение UNLIMITED в этом поле означает, что файл может расти, пока диск не будет заполнен.|  
|**рост**|**nvarchar(18)**|Значение прироста размера файла. Размер пространства, добавляемого в файл каждый раз, когда требуется новое пространство.|  
|**Использование**|**varchar(9)**|Применение файла. Для файла данных, значение равно **«данные»** и для файла журнала, — **только для журнал**.|  
  
## <a name="remarks"></a>Примечания  
 **Состояние** столбец результирующего набора отчетов, какие параметры установлен в значение ON в базе данных. Все параметры базы данных не сообщает о **состояние** столбца. Чтобы просмотреть полный список текущих параметров базы данных, используйте **sys.databases** представления каталога.  
  
## <a name="permissions"></a>Разрешения  
 При указании отдельной базы данных, членство в **открытый** роли в базе данных является обязательным. Если база данных не указан, членство в группе **открытый** роль в **master** необходима база данных.  
  
 Если база данных недоступна, **sp_helpdb** отображает сведения об ошибке номер 15622 и о базе данных, как это возможно.  
  
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
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
