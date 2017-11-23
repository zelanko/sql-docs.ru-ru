---
title: "sysmail_help_profile_sp (Transact-SQL) | Документы Microsoft"
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
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
caps.latest.revision: "41"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34dc0365eab64acf81dcb2dce24c8df38bd95e92
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpprofilesp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об одном или нескольких профилях электронной почты.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@profile_id**  =] *profile_id*  
 Идентификатор профиля, для которого возвращаются сведения. *profile_id* — **int**, значение по умолчанию NULL.  
  
 [  **@profile_name**  =] **"***profile_name***"**  
 Имя профиля, для которого возвращаются сведения. *profile_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор со следующими столбцами.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Description|  
|**profile_id**|**int**|Идентификатор профиля.|  
|**name**|**sysname**|Имя профиля.|  
|**Описание**|**nvarchar(256)**|Описание профиля.|  
  
## <a name="remarks"></a>Замечания  
 Если указано имя профиля или его идентификатор профиля, **sysmail_help_profile_sp** возвращает сведения об этом профиле. В противном случае **sysmail_help_profile_sp** возвращает сведения о каждом профиле в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
 Хранимая процедура **sysmail_help_profile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Список всех профилей**  
  
 Этот пример отображает список всех профилей экземпляра.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Далее приведен образец результирующего набора, повторно форматированный под длину строки:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **Б. Отображение конкретного профиля**  
  
 Этот пример отображает сведения для профиля `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Далее приведен образец результирующего набора, повторно форматированный под длину строки:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Компонент Database Mail хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
