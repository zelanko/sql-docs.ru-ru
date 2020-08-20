---
description: sp_markpendingschemachange (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b9e62684057772d18a78694de67928073bc10c8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489235"
---
# <a name="sp_markpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @schemaversion = ] schemaversion` Определяет ожидающее изменение схемы. *schemaVersion* имеет **тип int**и значение по умолчанию **0**. Используйте [sp_enumeratependingschemachanges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) , чтобы вывести список ожидающих изменений схемы для публикации.  
  
`[ @status = ] 'status'` Указывает, будет ли пропущено ожидающее изменение схемы. *состояние* — **nvarchar (10)** со значением по умолчанию **Active**. Если значение *Status* **пропущено**, то выбранное изменение схемы не будет реплицировано.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_markpendingschemachange** используется с репликацией слиянием.  
  
 **sp_markpendingschemachange** — это хранимая процедура, предназначенная для поддержки репликации слиянием и используемая только в том случае, если другие корректирующие действия, такие как повторная инициализация, не могли исправить ситуацию или имеют слишком много ресурсов в плане производительности.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_markpendingschemachange**.  
  
## <a name="see-also"></a>См. также  
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
