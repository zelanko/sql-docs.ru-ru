---
title: "sp_xp_cmdshell_proxy_account (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2aa36f38df0fdf1f36e5cfddc48044222d9509c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spxpcmdshellproxyaccount-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает учетные данные прокси-сервера для **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** отключена по умолчанию. Чтобы включить **xp_cmdshell**, в разделе [параметр конфигурации сервера «xp_cmdshell»](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 NULL  
 Указывает, что учетные данные учетной записи-посредника должны быть удалены.  
  
 *account_name*  
 Указывает имя входа Windows, которое будет использовано как учетная запись-посредник.  
  
 *пароль*  
 Указывает пароль для учетной записи Windows.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Учетные данные прокси-сервера будет вызываться **# #xp_cmdshell_proxy_account ##**.  
  
 Во время выполнения с помощью параметра NULL **sp_xp_cmdshell_proxy_account** удаляет учетные данные прокси-сервера.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-the-proxy-credential"></a>A. Создание учетных данных для учетной записи-посредника  
 Следующий пример показывает, как создать учетные данные учетной записи-посредника для учетной записи Windows с именем `ADVWKS\Max04` и паролем `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>Б. Удаление учетных данных для учетной записи-посредника  
 Следующий пример удаляет учетные данные учетной записи-посредника из хранилища учетных данных.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [xp_cmdshell &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
