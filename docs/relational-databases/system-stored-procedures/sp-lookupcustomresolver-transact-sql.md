---
title: sp_lookupcustomresolver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7f1bfc868b34ac16e1c38aedc9193002d35d5b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62959697"
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об обработчике бизнес-логики или о значении идентификатора класса (CLSID) компонента пользовательского сопоставителя на основе COM, который зарегистрирован у распространителя. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @article_resolver = ] 'article_resolver'` Задает имя пользовательской бизнес-логики, в которой проводится Отмена регистрации. *article_resolver* — **nvarchar(255)** , не имеет значения по умолчанию. Если удаляемая бизнес-логика является компонентом COM, то этим аргументом является понятное имя компонента. Если бизнес-логика представляет собой сборку [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, то этим аргументом является имя сборки.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT` Значение идентификатора CLSID объекта COM, связанного с именем пользовательской бизнес-логики, указанной в *article_resolver* параметра. *resolver_clsid* — **nvarchar(50)** , значение по умолчанию NULL.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT` Указывает тип пользовательской бизнес-логики регистрируется. *is_dotnet_assembly* — **бит**, значение по умолчанию 0. **1** указывает, что регистрируемая пользовательских бизнес-логика обработчика бизнес-логики сборкой. **0** означает, что COM-компонента.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT` — Имя сборки, реализующей обработчик бизнес-логики. *dotnet_assembly_name* — **nvarchar(255)** , со значением по умолчанию NULL.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT` Имя класса, переопределяющего <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для реализации обработчика бизнес-логики. *dotnet_class_name* — **nvarchar(255)** , со значением по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, со значением по умолчанию NULL. Используйте данный аргумент, если хранимая процедура не вызвана из издателя. Если этот аргумент не указан, то издателем считается локальный сервер.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_lookupcustomresolver** используется в репликации слиянием.  
  
 **sp_lookupcustomresolver** возвращает значение NULL для *resolver_clsid* Если компонент не зарегистрирован в распространителе и значение «00000000-0000-0000-0000-000000000000» Если регистрация относится к Сборки .NET framework зарегистрирован как обработчик бизнес-логики.  
  
 **sp_lookupcustomresolver** вызывается [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) и [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) для подтверждения указанного *article_resolver*.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** предопределенной роли базы данных в базе данных публикации могут выполнять процедуру **sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>См. также  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Выполнение бизнес-логики при синхронизации слиянием](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Указать Сопоставитель слияния статей](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
