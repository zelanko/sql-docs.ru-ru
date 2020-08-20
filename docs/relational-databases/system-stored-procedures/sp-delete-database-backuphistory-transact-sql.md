---
description: sp_delete_database_backuphistory (Transact-SQL)
title: sp_delete_database_backuphistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_database_backuphistory
- sp_delete_database_backuphistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_backuphistory
ms.assetid: 4c237944-453d-49fb-8d0e-4596945ac147
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a820a9a1da8a3938835f02a68d481b5f88790d4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493331"
---
# <a name="sp_delete_database_backuphistory-transact-sql"></a>sp_delete_database_backuphistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет сведения об указанной базе данных из таблиц журнала резервного копирования и восстановления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_database_backuphistory [ @database_name = ] 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database_name = ] database_name` Указывает имя базы данных, участвующей в операциях резервного копирования и восстановления. Аргумент *database_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_delete_database_backuphistory** должны запускаться из базы данных **msdb** .  
  
 Эта хранимая процедура влияет на следующие таблицы:  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile;](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory.](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются все элементы базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в таблицах журналов резервного копирования и восстановления.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_database_backuphistory @database_name = 'AdventureWorks2012';  
  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
