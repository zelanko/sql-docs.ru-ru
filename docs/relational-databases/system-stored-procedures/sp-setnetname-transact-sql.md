---
title: sp_setnetname (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 80a774ff85af1b696d018f8bd2159f509e1d5d27
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spsetnetname-transact-sql"></a>Хранимая процедура sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Присваивает сетевым именам **sys.servers** для их фактического сетевые имена компьютеров для удаленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта процедура может быть использована для разрешения выполнения вызовов удаленных хранимых процедур тем компьютерам, сетевые имена которых содержат неверные идентификаторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 **@server = "** *сервера* **"**  
 Имя удаленного сервера в синтаксисе вызова удаленных хранимых процедур, написанных пользователем. Только одну строку в **sys.servers** уже должен существовать для использования этой *сервера*. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 **@netname = "** *имя_сети* **"**  
 Сетевое имя компьютера, на который направляются вызовы удаленных хранимых процедур. *имя_сети* — **sysname**, не имеет значения по умолчанию.  
  
 Это имя должно совпадать с именем компьютера [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и может содержать символы, использование которых в качестве идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрещено.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Некоторые удаленные хранимые процедуры, обращающиеся к Windows-компьютерам, могут вызвать проблемы, если имя компьютера содержит недопустимые символы.  
  
 Так как связанные серверы размещены в одном пространстве имен, они не могут иметь одинаковое имя. Тем не менее, можно определить как связанный сервер, так и удаленного сервера с указанного сервера, назначив другие имена и с помощью **sp_setnetname** для присвоения сетевого имени одного из них сетевому имени базового сервера.  
  
```  
--Assume sqlserv2 is actual name of SQL Server   
--database server  
EXEC sp_addlinkedserver 'sqlserv2';  
GO  
EXEC sp_addserver 'rpcserv2';  
GO  
EXEC sp_setnetname 'rpcserv2', 'sqlserv2';  
```  
  
> [!NOTE]  
>  С помощью **sp_setnetname** для переключения связанного сервера обратно на локальный сервер не поддерживается. Серверы, которые описаны таким образом, не могут участвовать в распределенной транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** и **setupadmin** предопределенных ролей сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показана типичная административная последовательность, используемая в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для вызова удаленной хранимой процедуры.  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
