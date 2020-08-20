---
description: sp_changedistributor_property (Transact-SQL)
title: sp_changedistributor_property (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistributor_property_TSQL
- sp_changedistributor_property
helpviewer_keywords:
- sp_changedistributor_property
ms.assetid: 04f503a1-307c-4de0-bac6-e6e97d5b6940
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 284f669f81f0954c0a9676d5f7a4ab8a213eba58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464442"
---
# <a name="sp_changedistributor_property-transact-sql"></a>sp_changedistributor_property (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Изменяет свойства распространителя. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changedistributor_property [ [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @property = ] 'property'` Свойство для заданного распространителя. Аргумент *Property* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**heartbeat_interval**|Максимальное время работы агента (в минутах) без регистрации сообщения о ходе выполнения.|  
|NULL (по умолчанию)|Выводятся все доступные значения *свойств* .|  
  
`[ @value = ] 'value'` Значение для заданного свойства распространителя. *значение* имеет тип **varchar (255)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_changedistributor_property** используется во всех типах репликации.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/sp-changedistributor-pro_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changedistributor_property**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
