---
title: sp_registercustomresolver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3eac29c10b8f0204b3516051981fc29b3bee3ddc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751713"
---
# <a name="sp_registercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @article_resolver = ] 'article_resolver'`Указывает понятное имя регистрируемой настраиваемой бизнес-логики. *article_resolver* имеет тип **nvarchar (255)** и не имеет значения по умолчанию.  
  
`[ @resolver_clsid = ] 'resolver_clsid'`Указывает значение CLSID регистрируемого объекта COM. Настраиваемая бизнес-логика *resolver_clsid* имеет тип **nvarchar (50)** и значение по умолчанию NULL. Значение этого аргумента должно быть равным допустимому идентификатору CLSID или NULL (в случае регистрации сборки обработчиков бизнес-логики).  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly'`Указывает тип регистрируемой пользовательской бизнес-логики. *is_dotnet_assembly* аргумент имеет тип **nvarchar (50)** и значение по умолчанию false. **значение true** указывает, что регистрируемая настраиваемая бизнес-логика является сборкой обработчика бизнес-логики. **значение false** указывает, что это COM-компонент.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name'`Имя сборки, реализующей обработчик бизнес-логики. *dotnet_assembly_name* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  Если полный путь к сборке не описан в том же каталоге, что и исполняемый объект агента слияния, необходимо указать его в каталоге приложения, синхронно запускающего агент слияния, или в глобальном кэше сборок (GAC).  
  
`[ @dotnet_class_name = ] 'dotnet_class_name'`Имя класса, переопределяющего <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для реализации обработчика бизнес-логики. Имя должно быть указано в формате **Namespace. ClassName**. *dotnet_class_name* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_registercustomresolver** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_registercustomresolver**.  
  
## <a name="see-also"></a>См. также  
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Реализация пользовательского сопоставителя конфликтов для статьи публикации слиянием](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
