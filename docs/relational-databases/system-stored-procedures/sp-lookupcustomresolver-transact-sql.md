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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b86fd5bd04c41d10437a8a0f7bcc21b61ab22fef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720233"
---
# <a name="sp_lookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @article_resolver = ] 'article_resolver'`Указывает имя пользовательской бизнес-логики, для которой отменяется регистрация. *article_resolver* имеет тип **nvarchar (255)** и не имеет значения по умолчанию. Если удаляемая бизнес-логика является компонентом COM, то этим аргументом является понятное имя компонента. Если бизнес-логика представляет собой сборку [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, то этим аргументом является имя сборки.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT`Значение CLSID объекта COM, связанного с именем пользовательской бизнес-логики, указанной в параметре *article_resolver* . *resolver_clsid* имеет тип **nvarchar (50)** и значение по умолчанию NULL.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT`Указывает тип регистрируемой пользовательской бизнес-логики. *is_dotnet_assembly* имеет **бит**и значение по умолчанию 0. значение **1** указывает, что регистрируемая настраиваемая бизнес-логика является сборкой обработчика бизнес-логики. значение **0** указывает, что это COM-компонент.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT`Имя сборки, реализующей обработчик бизнес-логики. *dotnet_assembly_name* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT`Имя класса, переопределяющего <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для реализации обработчика бизнес-логики. *dotnet_class_name* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и значение по умолчанию NULL. Используйте данный аргумент, если хранимая процедура не вызвана из издателя. Если этот аргумент не указан, то издателем считается локальный сервер.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_lookupcustomresolver** используется в репликации слиянием.  
  
 **sp_lookupcustomresolver** ВОЗВРАЩАЕТ значение NULL для *resolver_clsid* , если компонент не зарегистрирован в распределении, и значение "00000000-0000-0000-0000-000000000000", если регистрация относится к .NET Framework сборке, зарегистрированной в качестве обработчика бизнес-логики.  
  
 **sp_lookupcustomresolver** вызывается [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) и [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) для проверки указанного *article_resolver*.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** в базе данных публикации могут выполнять **sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>См. также  
 [Расширенное обнаружение и разрешение конфликтов при репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Выполнение бизнес-логики во время синхронизации слиянием](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Указание арбитра статей публикации слиянием](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
