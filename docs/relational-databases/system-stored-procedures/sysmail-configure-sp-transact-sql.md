---
title: sysmail_configure_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_configure_sp_TSQL
- sysmail_configure_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_configure_sp
ms.assetid: 73b33c56-2bff-446a-b495-ae198ad74db1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df5b364408b012a186ca090b6d3a6d7de77119cf
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87122461"
---
# <a name="sysmail_configure_sp-transact-sql"></a>sysmail_configure_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет настройки конфигурации компонента Database Mail. Параметры конфигурации, заданные параметром **sysmail_configure_sp** , применяются ко всему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляру.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_configure_sp [ [ @parameter_name = ] 'parameter_name' ]  
    [ , [ @parameter_value = ] 'parameter_value' ]  
    [ , [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@parameter_name** =] **"**_parameter_name_**"**  
 Имя параметра, которое необходимо изменить.  
  
 [ **@parameter_value** =] **"**_parameter_value_**"**  
 Новое значение параметра.  
  
 [ **@description** =] **"**_Описание_**"**  
 Описание параметра.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Компонент Database Mail использует следующие параметры:  
  
| Имя параметра | Описание | Значение по умолчанию |
| -------------- | ----------- | ------------- |
|*AccountRetryAttempts*|Число попыток, предпринимаемых процессом внешней почты для отправки сообщения электронной почты с использованием каждой учетной записи в указанном профиле.|**1**|  
|*AccountRetryDelay*|Время ожидания процесса внешней почты между попытками отправить сообщение (в секундах).|**5000**|  
|*Параметре DatabaseMailExeMinimumLifeTime*|Минимальное время в секундах, в течение которого остается активным процесс внешней почты. Когда компонент Database Mail рассылает большое количество сообщений, необходимо увеличить это значение, чтобы поддержать этот компонент в активном состоянии и избежать дополнительной нагрузки из-за частых остановок и запусков.|**600**|  
|*дефаултаттачментенкодинг*|Кодировка для вложений электронной почты, используемая по умолчанию.|MIME|  
|*MaxFileSize*|Максимальный размер вложения в байтах.|**1000000**|  
|*прохибитедекстенсионс*|Разделенный запятыми список расширений файлов, которые невозможно отправить в виде вложений в сообщение электронной почты.|**EXE, DLL, VBS, JS**|  
|*LoggingLevel*|Укажите, какие сообщения записываются в журнал компонента Database Mail. Одно из следующих числовых значений:<br /><br /> 1 — Обычный режим. Регистрируются только ошибки.<br /><br /> 2 — Расширенный режим. Регистрируются ошибки, предупреждения и информационные сообщения.<br /><br /> 3 — Подробный режим. Регистрируются ошибки, предупреждения, информационные сообщения, сообщения об успешном выполнении и дополнительные внутренние сообщения. Используйте данный режим для диагностики.|**2**|  
  
 Хранимая процедура **sysmail_configure_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Настройка компонента Database Mail на повторение попытки 10 раз для каждой учетной записи**  
  
 В следующем примере показана настройка компонента Database Mail на повторение попытки для каждой учетной записи десять раз, прежде чем она будет воспринята как недоступная.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'AccountRetryAttempts', '10' ;  
```  
  
 **Б. Установка максимального размера вложения на 2 мегабайта**  
  
 В следующем примере показана установка максимального размера вложения на 2 мегабайта.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'MaxFileSize', '2097152' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_help_configure_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
