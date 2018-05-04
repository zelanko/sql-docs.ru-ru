---
title: sp_repltrans (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 00bc0a5fbc86d1e1d1aebcfac801e49fd975a4b3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 **sp_repltrans** возвращает сведения о базе данных публикации, из которой он выполняется, что позволяет просматривать нераспределенные в настоящее время транзакции (транзакции, остающиеся в журнале транзакций, который еще не отправлены Распространитель). Результирующий набор отображает регистрационный номер транзакций в журнале для первой и последней записи по каждой транзакции. **sp_repltrans** аналогичен [sp_replcmds &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) , но не возвращает команды транзакций.  
  
## <a name="remarks"></a>Замечания  
 **sp_repltrans** используется в репликации транзакций.  
  
 **sp_repltrans** не поддерживается для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_repltrans**.  
  
## <a name="see-also"></a>См. также  
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
