---
title: sp_markpendingschemachange (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e3bfd0bb51e6d269b84fdb57a5a64139ce23cedc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spmarkpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для поддержки публикаций слиянием, позволяя администратору пропустить выбранные изменения схемы, ожидающие завершения, чтобы избежать их реплицирования. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!CAUTION]  
>  Эта хранимая процедура позволяет не производить репликацию изменений схемы. Ее следует использовать для устранения проблем после того, как были испробованы другие методы, такие как повторная инициализация, или если эти методы являются слишком затратными с точки зрения их выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [**@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@schemaversion=** ] *schemaversion*  
 Идентифицирует отложенное изменение схемы. *schemaversion* — **int**, со значением по умолчанию **0**. Используйте [sp_enumeratependingschemachanges &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) списка отложенные изменения схемы для публикации.  
  
 [  **@status=** ] **"***состояние***"**  
 Обозначает, будет ли пропущено отложенное изменение схемы. *состояние* — **nvarchar(10)** со значением по умолчанию **active**. Если значение *состояние* — **пропущен**, то выбранное изменение схемы не будут реплицированы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_markpendingschemachange** используется с репликацией слиянием.  
  
 **sp_markpendingschemachange** хранимой процедуры предназначены для поддержки репликации слиянием и должна использоваться только в том случае, когда других корректирующих действий, таких как повторная инициализация, не удалось исправить ситуацию или являются слишком затратными в условия производительности.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_markpendingschemachange**.  
  
## <a name="see-also"></a>См. также  
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
