---
title: managed_backup.sp_backup_on_demand (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.sp_backup_on_demand
- smart_admin.sp_backup_on_demand_TSQL
- sp_backup_on_demand_TSQL
- sp_backup_on_demand
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.sp_backup_on_demand
- sp_backup_on_demand
ms.assetid: 638f809f-27fa-4c44-a549-9cf37ecc920c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a82c376481b5c0bb563ea5c48be8053d70f0d52
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636572"
---
# <a name="managedbackupspbackupondemand-transact-sql"></a>managed_backup.sp_backup_on_demand (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Запрашивает у компонента [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] выполнение резервного копирования указанной базы данных.  
  
 Эта хранимая процедура используется для выполнения нерегламентированного резервного копирования для базы данных, настроенной с помощью компонента [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Она предотвращает прерывание цепочки резервного копирования, учитывается процессами компонента [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] и сохраняет резервную копию в том же контейнере хранилища больших двоичных объектов Windows Azure.  
  
 При успешном завершении резервного копирования возвращается полный путь к файлу резервной копии. В него включено имя и местоположение нового файла резервной копии, созданного в операции резервного копирования.  
  
 Если [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] находится в процессе выполнения резервного копирования данного типа для указанной базы данных, возвращается ошибка. В этом случае возвращаемое сообщение об ошибке включает полный путь к файлу резервной копии, по которому будет загружена текущая резервная копия.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a> Аргументы  
 @database_name  
 Имя базы данных, для которой будет выполняться резервное копирование. @database_name — **SYSNAME**.  
  
 @type  
 Тип выполняемой резервной копии: база данных или журнала. @type Параметр **NVARCHAR(32)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в **db_backupoperator** роли базы данных с помощью **ALTER ANY CREDENTIAL** разрешения, и **EXECUTE** разрешения на **sp_delete_ backuphistory**хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается запрос на резервное копирование базы данных «TestDB». В базе данных включен компонент [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 Для каждого фрагмента кода в поле атрибута языка выберите «tsql».  
  
  
