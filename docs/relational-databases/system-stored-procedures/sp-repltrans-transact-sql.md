---
title: sp_repltrans (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a98ac1b5c0a5ee51865a6b18d63efff55e12907
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53203683"
---
# <a name="sprepltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор всех транзакций из журнала транзакций базы данных публикации, которые помечены для репликации, но не были помечены как распространенные. Эта хранимая процедура выполняется в базе данных публикаций на сервере издателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_repltrans** возвращает сведения о базе данных публикации, из которой она выполняется, что позволяет просматривать нераспределенные в настоящее время транзакции (транзакции, остающиеся в журнале транзакций, которое не было отправлено в Распространитель). Результирующий набор отображает регистрационный номер транзакций в журнале для первой и последней записи по каждой транзакции. **sp_repltrans** аналогичен [sp_replcmds &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) , но не возвращает команды транзакций.  
  
## <a name="remarks"></a>Примечания  
 **sp_repltrans** используется в репликации транзакций.  
  
 **sp_repltrans** не поддерживается для отличных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_repltrans**.  
  
## <a name="see-also"></a>См. также  
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
