---
title: sp_helpmergepartition (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords:
- sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ef6a1192ac2216ff335a98709520f10610cb373
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027932"
---
# <a name="sphelpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о секции для указанной публикации слиянием. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@suser_sname=** ] **"***suser_sname***"**  
 Значение SUSER_SNAME, определяющее секцию. *SUSER_SNAME* — **sysname**, со значением по умолчанию NULL. Введите этот аргумент для ограничения результирующего набора. При этом будут отображаться только те секции, в которых SUSER_SNAME разрешается в указанное значение.  
  
> [!NOTE]  
>  Когда *suser_sname* предоставляется, *host_name* должен иметь значение NULL  
  
 [  **@host_name=** ] **"***host_name***"**  
 Значение HOST_NAME, определяющее секцию. *HOST_NAME* — **sysname**, со значением по умолчанию NULL. Введите этот аргумент для ограничения результирующего набора. При этом будут отображаться только те секции, в которых HOST_NAME разрешается в указанное значение.  
  
> [!NOTE]  
>  Когда *suser_sname* предоставляется, *host_name* должен иметь значение NULL  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**секции**|**int**|Идентифицирует секцию подписчика.|  
|**HOST_NAME**|**sysname**|Значение, используемое при создании секции для подписки, которая фильтруется по значению [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на стороне подписчика.|  
|**SUSER_SNAME**|**sysname**|Значение, используемое при создании секции для подписки, которая фильтруется по значению [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на стороне подписчика.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Расположение моментального снимка отфильтрованных данных для секции подписчика.|  
|**date_refreshed**|**datetime**|Дата последнего запуска задания моментального снимка, создающего моментальный снимок отфильтрованных данных для секции.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Идентифицирует задание, которое создает моментальный снимок отфильтрованных данных для секции.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergepartition** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helpmergepartition**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
