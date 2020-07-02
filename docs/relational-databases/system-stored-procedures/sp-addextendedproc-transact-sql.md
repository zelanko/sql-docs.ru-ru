---
title: sp_addextendedproc (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 715318b0b0ea38870317d05815845e1b6eaa3227
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760186"
---
# <a name="sp_addextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Регистрирует имя новой расширенной хранимой процедуры в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [интеграцию со средой CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @functname = ] 'procedure'`Имя функции для вызова в библиотеке динамической компоновки (DLL). *процедура* имеет тип **nvarchar (517)** и не имеет значения по умолчанию. При *необходимости можно* включить имя владельца в форму *owner. function*.  
  
`[ @dllname = ] 'dll'`Имя библиотеки DLL, содержащей функцию. *DLL* имеет тип **varchar (255)** и не имеет значения по умолчанию. Рекомендуется указывать полный путь DLL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 После создания расширенной хранимой процедуры ее необходимо добавить в с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью **sp_addextendedproc**. Дополнительные сведения см. [в разделе Добавление расширенной хранимой процедуры в SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Эту процедуру можно выполнить только в базе данных **master** . Для выполнения расширенной хранимой процедуры из базы данных, отличной от **master**, следует определить имя расширенной хранимой процедуры с помощью **master**.  
  
 **sp_addextendedproc** добавляет записи в представление каталога [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) , регистрируя имя новой расширенной хранимой процедуры с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Он также добавляет запись в представление каталога [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) .  
  
> [!IMPORTANT]  
>  Существующие DLL-библиотеки, которые зарегистрированы без указания полного пути, перестанут работать после обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Чтобы устранить эту проблему, используйте **sp_dropextendedproc** , чтобы отменить регистрацию библиотеки DLL, а затем повторно зарегистрируйте ее с помощью **sp_addextendedproc**, указав полный путь.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_addextendedproc**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется **xp_hello** расширенная хранимая процедура.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>См. также:  
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [ПРЕДОСТАВЛЕНИЕ &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [ОТОЗВАТЬ &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
