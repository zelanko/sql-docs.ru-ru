---
title: sp_changedistributor_property (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_changedistributor_property_TSQL
- sp_changedistributor_property
helpviewer_keywords:
- sp_changedistributor_property
ms.assetid: 04f503a1-307c-4de0-bac6-e6e97d5b6940
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9b28929c1d63b706e4002f1d3bdfa89817cf6d93
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spchangedistributorproperty-transact-sql"></a>sp_changedistributor_property (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства распространителя. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changedistributor_property [ [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@property=**] **"***свойство***"**  
 Свойство конкретного распространителя. *Свойство* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**heartbeat_interval**|Максимальное время работы агента (в минутах) без регистрации сообщения о ходе выполнения.|  
|NULL (по умолчанию)|Все доступные *свойства* значения выводятся на печать.|  
  
 [  **@value=**] **"***значение***"**  
 Значение конкретного свойства распространителя. *значение* — **varchar(255)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changedistributor_property** используется во всех типах репликации.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/sp-changedistributor-pro_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_changedistributor_property**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
