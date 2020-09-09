---
description: sp_unregister_custom_scripting (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1bb9545e4a74fdf6831317ee31f36488e781239d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547304"
---
# <a name="sp_unregister_custom_scripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Эта хранимая процедура удаляет определяемую пользователем пользовательскую хранимую процедуру или [!INCLUDE[tsql](../../includes/tsql-md.md)] файл скрипта, зарегистрированную путем выполнения [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @type = ] 'type'` Тип удаляемой пользовательской хранимой процедуры или скрипта. *тип* — **varchar (16)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**insert**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции INSERT.|  
|**update**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции UPDATE.|  
|**delete**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции DELETE.|  
|**custom_script**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется в конце триггера языка DDL.|  
  
`[ @publication = ] 'publication'` Имя публикации, для которой удаляется пользовательская хранимая процедура или скрипт. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @article = ] 'article'` Имя статьи, для которой удаляется пользовательская хранимая процедура или скрипт. Аргумент *article* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_unregister_custom_scripting** используется в моментальных снимках и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin** могут выполнять **sp_unregister_custom_scripting**.  
  
## <a name="see-also"></a>См. также  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
