---
title: sp_unregister_custom_scripting (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d28ff96d07aa1b7e65097fbf7946b40dfb56adea
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808746"
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура удаляет пользовательские пользовательскую хранимую процедуру или [!INCLUDE[tsql](../../includes/tsql-md.md)] файл скрипта, который был зарегистрирован с помощью [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@type** =] **"***тип***"**  
 Тип удаляемой пользовательской хранимой процедуры или скрипта. *Тип* — **varchar(16)**, по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**insert**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции INSERT.|  
|**Обновление**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции UPDATE.|  
|**delete**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции DELETE.|  
|**custom_script**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется в конце триггера языка DDL.|  
  
 [ **@publication** =] **"***публикации***"**  
 Имя публикации, для которой удаляется пользовательская хранимая процедура или скрипт. *Публикация* — **sysname**, значение по умолчанию NULL.  
  
 [ **@article** =] **"***статье***"**  
 Имя статьи, для которой удаляется пользовательская хранимая процедура или скрипт. *статья* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_unregister_custom_scripting** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных или **db_ddladmin** предопределенной роли базы данных могут выполнять процедуру **sp_ unregister_custom_scripting**.  
  
## <a name="see-also"></a>См. также  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
