---
title: sp_registercustomresolver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7873d4288addbeaaba44fc7030f140180458e301
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608752"
---
# <a name="spregistercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрируют обработчик бизнес-логики или пользовательский сопоставитель на основе COM, которые могут быть вызваны в процессе синхронизации репликации слиянием. Эта хранимая процедура выполняется на распространителе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_registercustomresolver [ @article_resolver = ] 'article_resolver'   
    [ , [ @resolver_clsid = ] 'resolver_clsid' ]  
    [ , [ @is_dotnet_assembly = ] 'is_dotnet_assembly' ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@article_resolver =** ] **"***article_resolver***"**  
 Указывает понятное имя регистрируемого пользовательского обработчика бизнес-логики. *article_resolver* — **nvarchar(255)**, не имеет значения по умолчанию.  
  
 [  **@resolver_clsid=** ] **"***resolver_clsid***"**  
 Указывает значение идентификатора CLSID регистрируемого объекта COM. Пользовательская бизнес-логика *resolver_clsid* — **nvarchar(50)**, значение по умолчанию NULL. Значение этого аргумента должно быть равным допустимому идентификатору CLSID или NULL (в случае регистрации сборки обработчиков бизнес-логики).  
  
 [  **@is_dotnet_assembly=** ] **"***is_dotnet_assembly***"**  
 Указывает тип регистрируемой пользовательской бизнес-логики. *is_dotnet_assembly* — **nvarchar(50)**, значение по умолчанию FALSE. **значение true,** указывает, что регистрируемая пользовательских бизнес-логика обработчика бизнес-логики сборкой. **false** означает, что COM-компонента.  
  
 [  **@dotnet_assembly_name=** ] **"***dotnet_assembly_name***"**  
 Имя сборки, в которой реализован обработчик бизнес-логики. *dotnet_assembly_name* — **nvarchar(255)**, со значением по умолчанию NULL. Если полный путь к сборке не описан в том же каталоге, что и исполняемый объект агента слияния, необходимо указать его в каталоге приложения, синхронно запускающего агент слияния, или в глобальном кэше сборок (GAC).  
  
 [  **@dotnet_class_name=** ] **"***dotnet_class_name***"**  
 Имя класса, который замещает класс <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для реализации обработчика бизнес-логики. Следует указать имя в форме **пространствоИмен.ИмяКласса**. *dotnet_class_name* — **nvarchar(255)**, со значением по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_registercustomresolver** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_registercustomresolver**.  
  
## <a name="see-also"></a>См. также  
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
