---
title: sp_markpendingschemachange (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67377f638459a37f25fbc78b9acff395192a2f3f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537336"
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
  
`[ @schemaversion = ] schemaversion` Идентифицирует отложенное изменение схемы. *schemaversion* — **int**, со значением по умолчанию **0**. Используйте [sp_enumeratependingschemachanges &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) Чтобы получить список отложенные изменения схемы для публикации.  
  
`[ @status = ] 'status'` Обозначает, будет ли пропущено отложенное изменение схемы. *состояние* — **nvarchar(10)** со значением по умолчанию **active**. Если значение *состояние* — **пропущено**, то выбранное изменение схемы не будут реплицированы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_markpendingschemachange** используется с репликацией слиянием.  
  
 **sp_markpendingschemachange** хранимой процедуры, предназначенной для поддержки репликации слиянием и должен использоваться только в том случае, если другие действия по исправлению, таких как повторная инициализация, не удалось исправить ситуацию или являются слишком затратными в условия производительности.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_markpendingschemachange**.  
  
## <a name="see-also"></a>См. также  
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
