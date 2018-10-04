---
title: sysmail_help_configure_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ef80206f9ff82cf1ab2917e90f61432be15c190
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838432"
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
 [**@parameter_name** =] **"***parameter_name***"**  
 Имя параметра конфигурации, значение которого нужно получить. Если он указан, значение параметра конфигурации возвращается в **@parameter_value** ВЫХОДНОЙ параметр. Если аргумент **@parameter_name** указан, эта хранимая процедура возвращает результирующий набор, содержащий все параметры конфигурации компонента Database Mail в экземпляре.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если аргумент **@parameter_name** указан, возвращает результирующий набор со следующими столбцами.  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|**paramName**|**nvarchar(256)**|Имя параметра конфигурации.|  
|**ParamValue**|**nvarchar(256)**|Значение параметра конфигурации.|  
|**Описание**|**nvarchar(256)**|Описание параметра конфигурации.|  
  
## <a name="remarks"></a>Примечания  
 Хранимая процедура **sysmail_help_configure_sp** отображает список текущих параметров конфигурации компонента Database Mail для экземпляра.  
  
 Когда **@parameter_name** указано, но без выходного параметра предоставляется для **@parameter_value**, эта хранимая процедура не возвращает выходные данные.  
  
 Хранимая процедура **sysmail_help_configure_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедура должен вызываться с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
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
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
