---
title: sp_setnetname (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 140765eacad1d035f9e8640330701711a358991b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719208"
---
# <a name="sp_setnetname-transact-sql"></a>Хранимая процедура sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Устанавливает сетевые имена в **sys. Servers** на реальные имена сетевых компьютеров для удаленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта процедура может быть использована для разрешения выполнения вызовов удаленных хранимых процедур тем компьютерам, сетевые имена которых содержат неверные идентификаторы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 ** @server = '** *сервер* **'**  
 Имя удаленного сервера в синтаксисе вызова удаленных хранимых процедур, написанных пользователем. Для использования этого *сервера*уже должна существовать ровно одна строка в **sys.** Servers. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 ** @netname = '** *network_name* **'**  
 Сетевое имя компьютера, на который направляются вызовы удаленных хранимых процедур. Аргумент *network_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 Это имя должно совпадать с именем компьютера [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и может содержать символы, использование которых в качестве идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрещено.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Некоторые удаленные хранимые процедуры, обращающиеся к Windows-компьютерам, могут вызвать проблемы, если имя компьютера содержит недопустимые символы.  
  
 Так как связанные серверы размещены в одном пространстве имен, они не могут иметь одинаковое имя. Однако для указанного сервера можно определить как связанный сервер, так и удаленный сервер, назначив разные имена и используя **sp_setnetname** , чтобы задать сетевое имя одного из них в сетевое имя базового сервера.  
  
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
>  Использование **sp_setnetname** для указания связанного сервера обратно на локальный сервер не поддерживается. Серверы, которые описаны таким образом, не могут участвовать в распределенной транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенных ролях сервера **sysadmin** и **setupadmin** .  
  
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
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
