---
title: sys.sysdatabases (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b655cf84c63502af4f3944b3b490a9237af7d1d1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждой базы данных в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после установки **sysdatabases** содержит записи для **master**, **модели**, **msdb**и **tempdb** баз данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных|  
|**dbid**|**smallint**|Идентификатор базы данных|  
|**ИД безопасности**|**varbinary(85)**|Системный идентификатор создателя базы данных.|  
|**Режим**|**smallint**|Для внутреннего применения: блокирует базу данных во время ее создания.|  
|**status**|**int**|Биты состояния, некоторые из которых можно задать с помощью [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) иное:<br /><br /> 1 = **autoclose** (ALTER DATABASE)<br /><br /> 4 = **select в / bulkcopy** (ALTER DATABASE с помощью SET RECOVERY)<br /><br /> 8 = **trunc. журнала на контрольной точке** (ALTER DATABASE с помощью SET RECOVERY)<br /><br /> 16 = **обнаружение разорванных страниц** (ALTER DATABASE)<br /><br /> 32 = **загрузки**<br /><br /> 64 = **Подготовка к восстановлению**<br /><br /> 128 = **восстановление**<br /><br /> 256 = **не восстановлена.**<br /><br /> 512 = **автономного** (ALTER DATABASE)<br /><br /> 1024 = **только для чтения** (ALTER DATABASE)<br /><br /> 2048 = **используется только dbo** (ALTER DATABASE с помощью SET RESTRICTED_USER)<br /><br /> 4096 = **одного пользователя** (ALTER DATABASE)<br /><br /> 32768 = **аварийный режим**<br /><br /> 65536 = **КОНТРОЛЬНОЙ СУММЫ** (ALTER DATABASE)<br /><br /> 4194304 = **autoshrink** (ALTER DATABASE)<br /><br /> 1073741824 = **безопасное завершение работы**<br /><br /> В одно и то же время несколько битов могут находиться в состоянии ON.|  
|**status2**|**int**|16384 = **ANSI null по умолчанию** (ALTER DATABASE)<br /><br /> 65536 = **сцепление значений null дает null** (ALTER DATABASE)<br /><br /> 131072 = **рекурсивные триггеры** (ALTER DATABASE)<br /><br /> 1048576 = **по умолчанию локальный курсор** (ALTER DATABASE)<br /><br /> 8388608 = **заключенный в кавычки идентификатор** (ALTER DATABASE)<br /><br /> 33554432 = **закрытие курсора при фиксации** (ALTER DATABASE)<br /><br /> 67108864 = **ANSI nulls** (ALTER DATABASE)<br /><br /> 268435456 = **предупреждения ANSI** (ALTER DATABASE)<br /><br /> 536870912 = **полнотекстовые функции включены** (устанавливается с помощью **sp_fulltext_database**)|  
|**crdate**|**datetime**|Дата создания.|  
|**Зарезервировано**|**datetime**|Зарезервировано для последующего использования.|  
|**Категория**|**int**|Содержит битовую карту данных, применяемых при репликации:<br /><br /> 1 = опубликовано для репликации моментальных снимков или транзакций;<br /><br /> 2 = есть подписка на публикацию моментальных снимков или на публикации транзакций;<br /><br /> 4 = опубликовано для репликации слиянием;<br /><br /> 8 = есть подписка на публикацию слиянием;<br /><br /> 16 = база данных распространителя.|  
|**cmptlevel**|**tinyint**|Уровень совместимости для базы данных. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|  
|**Имя файла**|**nvarchar(260)**|Имя основного файла базы данных и путь к нему в операционной системе.<br /><br /> **Имя файла** является видимым для **dbcreator**, **sysadmin**, владелец базы данных с разрешениями CREATE ANY DATABASE или участникам, которым предоставлены следующие разрешения: ALTER ANY DATABASE СОЗДАНИЕ ЛЮБОЙ БАЗЫ ДАННЫХ, VIEW ANY DEFINITION. Чтобы получить путь и имя файла, запросите [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md) представление совместимости или [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) представления.|  
|**version**|**smallint**|Внутренний номер версии того кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которым была создана база данных. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
