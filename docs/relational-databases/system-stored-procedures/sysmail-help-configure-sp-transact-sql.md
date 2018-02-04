---
title: "sysmail_help_configure_sp (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13f768cd5e1cbbbcfa3f5b74d7ae52d2e9f357e1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailhelpconfiguresp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает настройки конфигурации компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [**@parameter_name** = ] **'***parameter_name***'**  
 Имя параметра конфигурации, значение которого нужно получить. Если указано, значение параметра конфигурации возвращается в  **@parameter_value**  ВЫХОДНОЙ параметр. Если аргумент  **@parameter_name**  указан, эта хранимая процедура возвращает результирующий набор, содержащий все параметры конфигурации компонента Database Mail в экземпляре.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если аргумент  **@parameter_name**  указан, то возвращает результирующий набор со следующими столбцами.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|**paramName**|**nvarchar(256)**|Имя параметра конфигурации.|  
|**paramvalue**|**nvarchar(256)**|Значение параметра конфигурации.|  
|**Описание**|**nvarchar(256)**|Описание параметра конфигурации.|  
  
## <a name="remarks"></a>Remarks  
 Хранимая процедура **sysmail_help_configure_sp** перечислены текущие параметры конфигурации компонента Database Mail для экземпляра.  
  
 Когда  **@parameter_name**  указан, но указан без выходного параметра, для  **@parameter_value** , эта хранимая процедура не возвращает результат.  
  
 Хранимая процедура **sysmail_help_configure_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедура должна вызываться с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере процедура отображает список параметров конфигурации компонента Database Mail для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
```  
paramname                       paramvalue      description  
------------------------------- --------------- -----------------------------------------------------------------------------  
AccountRetryAttempts            1               Number of retry attempts for a mail server  
AccountRetryDelay               5000            Delay between each retry attempt to mail server  
DatabaseMailExeMinimumLifeTime  600             Minimum process lifetime in seconds  
DefaultAttachmentEncoding       MIME            Default attachment encoding  
LoggingLevel                    2               Database Mail logging level: normal - 1, extended - 2 (default), verbose - 3  
MaxFileSize                     1000000         Default maximum file size  
ProhibitedExtensions            exe,dll,vbs,js  Extensions not allowed in outgoing mails  
  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Компонент Database Mail хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
