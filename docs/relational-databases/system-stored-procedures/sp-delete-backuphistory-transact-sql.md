---
description: sp_delete_backuphistory (Transact-SQL)
title: sp_delete_backuphistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_backuphistory
- sp_delete_backuphistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_backuphistory
ms.assetid: bdb56834-616e-47e4-b942-e895d2325e97
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be5b2d16d3a6131d6c579a7f4f3c422ac003da73
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493389"
---
# <a name="sp_delete_backuphistory-transact-sql"></a>sp_delete_backuphistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Уменьшает размер таблиц журнала резервного копирования и восстановления, удаляя записи для резервных наборов данных, которые старше указанной даты. Дополнительные строки добавляются в таблицы журнала резервного копирования и восстановления после выполнения каждой операции резервного копирования или восстановления. Поэтому рекомендуется периодически выполнять **sp_delete_backuphistory**.  
  
> [!NOTE]  
>  Таблицы журнала резервного копирования и восстановления находятся в базе данных **msdb** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_backuphistory [ @oldest_date = ] 'oldest_date'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @oldest_date = ] 'oldest\_date'` Самая старая Дата, сохраняемая в таблицах журнала резервного копирования и восстановления. *oldest_date* имеет тип **DateTime**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_delete_backuphistory** должны запускаться из базы данных **msdb** и влиять на следующие таблицы:  
  
-   [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile;](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory.](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
 Физические файлы резервных копий сохраняются, даже если удаляется весь журнал.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** , но разрешения могут предоставляться другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере из таблиц журнала резервного копирования и восстановления удаляются все записи, внесенные до 12:00 14 января 2010 года.  
  
```  
USE msdb;  
GO  
EXEC sp_delete_backuphistory @oldest_date = '01/14/2010';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_database_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
