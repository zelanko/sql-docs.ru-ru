---
title: managed_backup.fn_is_master_switch_on (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_is_master_switch_on
- fn_is_master_switch_on_TSQL
- smart_admin.fn_is_master_switch_on
- smart_admin.fn_is_master_switch_on_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_is_master_switch_on
- fn_is_master_switch_on
ms.assetid: e8c2108d-b104-46cb-9645-a15f46112c86
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1317e029b51f0e0abd2df97896533dafbf74a5a1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="managedbackupfnismasterswitchon-transact-sql"></a>managed_backup.fn_is_master_switch_on (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает состояние операций [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в экземпляре SQL Server.  
  
 Используйте эту функцию для получения текущего состояния [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.fn_is_master_switch_on ()  
```  
  
##  <a name="Arguments"></a> Аргументы  
 Нет  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **BIT**  
  
 1 = служба [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] активна, 0 = служба [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] приостановлена.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимы разрешения SELECT для функции.  
  
## <a name="see-also"></a>См. также  
 [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
