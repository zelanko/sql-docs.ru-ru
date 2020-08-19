---
description: Процедура sp_register_custom_scripting (Transact-SQL)
title: sp_register_custom_scripting (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 35e70da9de3239fa7f147acf8ffe5a6ecc724606
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446871"
---
# <a name="sp_register_custom_scripting-transact-sql"></a>Процедура sp_register_custom_scripting (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. После изменения схемы реплицируемой таблицы эти процедуры создаются снова. **sp_register_custom_scripting** регистрирует хранимую процедуру или [!INCLUDE[tsql](../../includes/tsql-md.md)] файл скрипта, который выполняется при изменении схемы для создания скрипта определения для новой пользовательской хранимой процедуры. Эта новая пользовательская хранимая процедура должна отражать новую схему таблицы. **sp_register_custom_scripting** выполняется на издателе в базе данных публикации, а зарегистрированный файл скрипта или хранимая процедура выполняются на подписчике при изменении схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @type = ] 'type'` Тип регистрируемой пользовательской хранимой процедуры или скрипта. *тип* — **varchar (16)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**insert**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции INSERT.|  
|**update**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции UPDATE.|  
|**delete**|Зарегистрированная пользовательская хранимая процедура, выполняющаяся при репликации инструкции DELETE.|  
|**custom_script**|Скрипт, выполняющийся в конце триггера языка DDL.|  
  
`[ @value = ] 'value'` Имя хранимой процедуры или имени и полный путь к [!INCLUDE[tsql](../../includes/tsql-md.md)] регистрируемому файлу скрипта. *value* имеет тип **nvarchar (1024)** и не имеет значения по умолчанию.  
  
> [!NOTE]  
>  При указании значения NULL для параметра *value*будет отменена регистрация ранее зарегистрированного скрипта, который совпадает с запуском [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Если значение *типа* — **custom_script**, ожидается имя и полный путь к [!INCLUDE[tsql](../../includes/tsql-md.md)] файлу скрипта. В противном случае *значение* должно быть именем зарегистрированной хранимой процедуры.  
  
`[ @publication = ] 'publication'` Имя публикации, для которой регистрируется пользовательская хранимая процедура или скрипт. Аргумент *publication* имеет тип **sysname**и значение по умолчанию **null**.  
  
`[ @article = ] 'article'` Имя статьи, для которой регистрируется пользовательская хранимая процедура или скрипт. Аргумент *article* имеет тип **sysname**и значение по умолчанию **null**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_register_custom_scripting** используется в моментальных снимках и репликации транзакций.  
  
 Эта хранимая процедура должна выполняться до внесения изменений в схему реплицируемой таблицы. Дополнительные сведения об использовании этой хранимой процедуры см. [в разделе повторное создание пользовательских процедур транзакций для отражения изменений схемы](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin** могут выполнять **sp_register_custom_scripting**.  
  
## <a name="see-also"></a>См. также:  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
