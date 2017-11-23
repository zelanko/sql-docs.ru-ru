---
title: "sp_delete_database_backuphistory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_database_backuphistory
- sp_delete_database_backuphistory_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_database_backuphistory
ms.assetid: 4c237944-453d-49fb-8d0e-4596945ac147
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 226504d79ccdbf49cbf68a9e32dd7036902f9416
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletedatabasebackuphistory-transact-sql"></a>sp_delete_database_backuphistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет сведения об указанной базе данных из таблиц журнала резервного копирования и восстановления.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://msdn.microsoft.com/library/bb500435.aspx)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_database_backuphistory [ @database_name = ] 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@database_name=** ] *имя_базы_данных*  
 Указывает имя базы данных, над которой производятся операции резервного копирования и восстановления. *database_name* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_database_backuphistory** должна запускаться из **msdb** базы данных.  
  
 Эта хранимая процедура влияет на следующие таблицы:  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile;](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory.](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются все элементы базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в таблицах журналов резервного копирования и восстановления.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_database_backuphistory @database_name = 'AdventureWorks2012';  
  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_backuphistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
