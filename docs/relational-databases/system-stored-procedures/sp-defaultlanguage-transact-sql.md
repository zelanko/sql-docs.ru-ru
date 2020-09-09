---
description: sp_defaultlanguage (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5eb94ea64b22f233d1c7c1e5d508fc0704f931ab
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549880"
---
# <a name="sp_defaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет установленный по умолчанию язык для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [инструкцию ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'` Имя входа. Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию. *именем входа* может быть существующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа или пользователь или группа Windows.  
  
`[ @language = ] 'language'` Язык по умолчанию для имени входа. *Language* имеет тип **sysname**и значение по умолчанию NULL. *язык* должен быть допустимым языком на сервере. Если *язык* не указан, для параметра *Language* задан язык сервера по умолчанию; язык по умолчанию определяется языком **sp_configure** переменной конфигурации **по умолчанию**. Изменение заданного по умолчанию языка сервера не изменяет язык, заданный по умолчанию для существующих имен входа.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_defaultlanguage** вызывает инструкцию ALTER LOGIN, которая поддерживает дополнительные параметры. Дополнительные сведения об изменении других значений по умолчанию для входа см. в разделе [ALTER login &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 Для изменения языка текущего сеанса воспользуйтесь инструкцией SET LANGUAGE. Используйте функцию @ @LANGUAGE для отображения текущего языкового параметра.  
  
 Если язык по умолчанию для имени входа удаляется с сервера, то имя входа приобретает текущий язык по умолчанию сервера. **sp_defaultlanguage** не может быть выполнена в пользовательской транзакции.  
  
 Сведения о языках, установленных на сервере, отображаются в представлении каталога **sys.sysязыки** .  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN.  
  
## <a name="examples"></a>Примеры  
 В следующем примере инструкция `ALTER LOGIN` используется для изменения языка по умолчанию для имени входа `Fathima` на арабский. Это является предпочтительным методом.  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN (Transact-SQL)](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE (Transact-SQL)](../../t-sql/functions/language-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [ Языкиsys.sys&#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
