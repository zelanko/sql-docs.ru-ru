---
title: sp_register_custom_scripting (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57a58ec761dfbc8a3db0a9bec01ffeb04dc9e0e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700552"
---
# <a name="spregistercustomscripting-transact-sql"></a>Процедура sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. После изменения схемы реплицируемой таблицы эти процедуры создаются снова. **sp_register_custom_scripting** регистрирует хранимую процедуру или [!INCLUDE[tsql](../../includes/tsql-md.md)] файл скрипта, который выполняется при изменении схемы в скрипт определения для новых пользовательских пользовательская хранимая процедура. Эта новая пользовательская хранимая процедура должна отражать новую схему таблицы. **sp_register_custom_scripting** выполняется на издателе в базе данных публикации, а зарегистрированный файл скрипта или хранимая процедура выполняется на подписчике при изменении схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@type** =] **"***тип***"**  
 Тип регистрируемой пользовательской хранимой процедуры или скрипта. *Тип* — **varchar(16)**, по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**insert**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции INSERT.|  
|**Обновление**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции UPDATE.|  
|**delete**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции DELETE.|  
|**custom_script**|Скрипт, выполняющийся в конце триггера языка DDL.|  
  
 [ **@value**=] **"***значение***"**  
 Имя хранимой процедуры или имя и полностью определенный путь к файлу скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] для регистрации. *значение* — **nvarchar(1024)**, не имеет значения по умолчанию.  
  
> [!NOTE]  
>  Указав значение NULL для *значение*параметр отменяет регистрацию зарегистрированного ранее сценарий, который является таким же, как работает [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Если значение *тип* — **custom_script**, имя и полный путь к [!INCLUDE[tsql](../../includes/tsql-md.md)] ожидается, что файл скрипта. В противном случае *значение* должно быть именем регистрируемой хранимой процедуры.  
  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации, для которой регистрируется пользовательская хранимая процедура или скрипт. *Публикация* — **sysname**, значение по умолчанию **NULL**.  
  
 [ **@article**=] **"***статье***"**  
 Имя статьи, для которой регистрируется пользовательская хранимая процедура или скрипт. *статья* — **sysname**, значение по умолчанию **NULL**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_register_custom_scripting** используется в репликации моментальных снимков и репликации транзакций.  
  
 Эта хранимая процедура должна выполняться до внесения изменений в схему реплицируемой таблицы. Дополнительные сведения об использовании этой хранимой процедуры см. в разделе [повторное создание пользовательских процедур транзакций с учетом изменений в схеме](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных или **db_ddladmin** предопределенной роли базы данных могут выполнять процедуру **sp_ register_custom_scripting**.  
  
## <a name="see-also"></a>См. также  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
