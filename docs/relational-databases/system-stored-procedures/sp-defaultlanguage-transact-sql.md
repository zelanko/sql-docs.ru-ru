---
title: sp_defaultlanguage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: af2402ce4f1e49ee572a9d271497c2798d679070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120093"
---
# <a name="spdefaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет установленный по умолчанию язык для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'` — Имя входа. *Имя входа* — **sysname**, не имеет значения по умолчанию. *Имя входа* может представлять собой существующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа или пользователя Windows или группы.  
  
`[ @language = ] 'language'` — Это язык по умолчанию для имени входа. *Язык* — **sysname**, значение по умолчанию NULL. *Язык* должен быть действительным языком на сервере. Если *языка* не указан, *языка* имеет значение по умолчанию язык сервера; язык по умолчанию определяется **sp_configure** переменную конфигурации **язык по умолчанию**. Изменение заданного по умолчанию языка сервера не изменяет язык, заданный по умолчанию для существующих имен входа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_defaultlanguage** вызывает инструкцию ALTER LOGIN, которая поддерживает дополнительные параметры. Сведения об изменении других значений по умолчанию для имени входа, см. в разделе [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
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
 [ALTER LOGIN (Transact-SQL)](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE (Transact-SQL)](../../t-sql/functions/language-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
