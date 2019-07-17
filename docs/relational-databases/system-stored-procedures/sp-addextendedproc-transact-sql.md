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
ms.openlocfilehash: 0bc8ea22699762927a026ae4cc811500c193555c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072755"
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрирует имя новой расширенной хранимой процедуры [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте вместо этого [интеграцию со средой CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @functname = ] 'procedure'` — Имя функции, вызываемой в библиотеке динамической компоновки (DLL). *процедура* — **nvarchar(517)** , не имеет значения по умолчанию. *процедура* может также включать имя владельца в форме *owner.function*.  
  
`[ @dllname = ] 'dll'` — Имя библиотеки DLL, содержащей функцию. *библиотеки DLL* — **varchar(255)** , не имеет значения по умолчанию. Рекомендуется указывать полный путь DLL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 После создания расширенной хранимой процедуры, его необходимо добавить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью **sp_addextendedproc**. Дополнительные сведения см. в разделе [Добавление расширенную хранимую процедуру в SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Эта процедура может выполняться только в **master** базы данных. Для выполнения расширенной хранимой процедуры из базы данных, отличных от **master**, используйте в имени расширенной хранимой процедуры с **master**.  
  
 **sp_addextendedproc** добавляет записи в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представление каталога, регистрация имени новой расширенной хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он также добавляет запись в [sys.extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) представления каталога.  
  
> [!IMPORTANT]  
>  Существующие DLL-библиотеки, которые зарегистрированы без указания полного пути, перестанут работать после обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Чтобы устранить проблему, используйте **sp_dropextendedproc** для отмены регистрации библиотеки DLL, а затем выполните их повторную регистрацию с помощью **sp_addextendedproc**, указав полный путь.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_addextendedproc**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется **xp_hello** расширенной хранимой процедуры.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>См. также  
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
