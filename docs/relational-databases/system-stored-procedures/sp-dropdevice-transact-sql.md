---
title: sp_dropdevice (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropdevice_TSQL
- sp_dropdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], deleting
- sp_dropdevice
ms.assetid: c8b07189-7c35-414b-acc1-45bd6e7e17c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9be64080f6e1c56daa0901dbdc174c83d40cf541
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85859986"
---
# <a name="sp_dropdevice-transact-sql"></a>sp_dropdevice (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет устройство базы данных или устройство резервного копирования из экземпляра [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)] , удаляя запись с **master.dbo.sysустройств**.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropdevice [ @logicalname = ] 'device'   
    [ , [ @delfile = ] 'delfile' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @logicalname = ] 'device'`Логическое имя устройства базы данных или устройства резервного копирования, указанное в **master.dbo.sysDevices.Name**. Аргумент *Device* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @delfile = ] 'delfile'`Указывает, следует ли удалить файл физического устройства резервного копирования. *DELFILE* имеет тип **varchar (7)**. При указании в качестве **DELFILE**файл диска физического устройства резервного копирования удаляется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_dropdevice** нельзя использовать внутри транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере из компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] удаляется устройство хранения на магнитной ленте `tapedump1`.  
  
```  
EXEC sp_dropdevice 'tapedump1';  
```  
  
## <a name="see-also"></a>Дополнительно  
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Удаление SQL Server &#40;устройства резервного копирования&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)   
 [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdevice-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
