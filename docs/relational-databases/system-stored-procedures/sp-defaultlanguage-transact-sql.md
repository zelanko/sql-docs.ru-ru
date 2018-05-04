---
title: sp_defaultlanguage (Transact-SQL) | Документы Microsoft
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
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f5dce9e59e4fbc5cfd9a0fcd06c367f2488d7246
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdefaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет установленный по умолчанию язык для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame =** ] **"***входа***"**  
 Имя входа. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* может быть существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или пользователя Windows или группы.  
  
 [  **@language =** ] **"***языка***"**  
 Язык по умолчанию для имени входа. *Язык* — **sysname**, значение по умолчанию NULL. *Язык* должен быть языком, допустимым на сервере. Если *язык* не указан, *язык* задано значение по умолчанию язык сервера; язык по умолчанию определяется **sp_configure** переменной конфигурации **язык по умолчанию**. Изменение заданного по умолчанию языка сервера не изменяет язык, заданный по умолчанию для существующих имен входа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_defaultlanguage** вызывает инструкцию ALTER LOGIN, которая поддерживает дополнительные параметры. Сведения об изменении других значений по умолчанию для имени входа см. в разделе [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 Для изменения языка текущего сеанса воспользуйтесь инструкцией SET LANGUAGE. Используйте @@LANGUAGE функции для отображения текущих языковых параметров.  
  
 Если язык по умолчанию для имени входа удаляется с сервера, то имя входа приобретает текущий язык по умолчанию сервера. **sp_defaultlanguage** не может выполняться внутри пользовательской транзакции.  
  
 Сведения о языках, установленных на сервере можно увидеть в **sys.syslanguages** представления каталога.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN.  
  
## <a name="examples"></a>Примеры  
 В следующем примере инструкция `ALTER LOGIN` используется для изменения языка по умолчанию для имени входа `Fathima` на арабский. Этот метод является предпочтительным.  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
