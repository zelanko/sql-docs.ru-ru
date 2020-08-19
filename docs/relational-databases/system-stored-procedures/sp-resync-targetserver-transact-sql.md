---
description: sp_resync_targetserver (Transact-SQL)
title: sp_resync_targetserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_resync_targetserver
- sp_resync_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resync_targetserver
ms.assetid: 40e44df7-d3e3-44ee-b149-08aba629a21f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 858c2ffe0740c43892ff2245047823c9cecbd12a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469238"
---
# <a name="sp_resync_targetserver-transact-sql"></a>sp_resync_targetserver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Повторно синхронизирует многосерверные задания на указанном целевом сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_resync_targetserver  
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @server_name = ] 'server'` Имя сервера для повторной синхронизации. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию. Если указано значение **ALL** , то повторно синхронизируются все целевые серверы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Сообщает результат действий **sp_post_msx_operation** .  
  
## <a name="remarks"></a>Remarks  
 **sp_resync_targetserver** удаляет текущий набор инструкций для целевого сервера и отправляет новый набор для загрузки целевым сервером. Новый набор состоит из инструкции для удаления всех многосерверных заданий, за которой следуют вставки, по одной для каждого текущего задания для целевого сервера.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере повторно синхронизируется целевой сервер `SEATTLE1`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_resync_targetserver  
    N'SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_help_downloadlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)   
 [sp_post_msx_operation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
