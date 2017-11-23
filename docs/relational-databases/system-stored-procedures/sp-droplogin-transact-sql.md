---
title: "sp_droplogin (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_droplogin
- sp_droplogin_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_droplogin
ms.assetid: e58684d1-c394-48de-906e-da6ee91100c3
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1dffca95e1623b8177359e5f327ddd7df774e28
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdroplogin-transact-sql"></a>sp_droplogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это предотвращает доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с этим именем входа.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) вместо него.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droplogin [ @loginame = ] 'login'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame =** ] **"***входа***"**  
 Имя входа для удаления. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* уже должен существовать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_droplogin** вызывает инструкцию DROP LOGIN.  
  
 **sp_droplogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с помощью инструкции `DROP LOGIN` удаляется имя входа `Victoria` из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот метод является предпочтительным.  
  
```  
DROP LOGIN Victoria;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
