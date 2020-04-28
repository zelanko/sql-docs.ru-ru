---
title: sysmail_start_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e15996a9db6e1b782875f2dd3d73d0e3e514c8f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68044437"
---
# <a name="sysmail_start_sp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Начинает выполнение компонента Database Mail, запуская объекты [!INCLUDE[ssSB](../../includes/sssb-md.md)], используемые внешней программой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Компонент Database Mail не включен, или не установлен, или не включен в установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы включить и установить объекты компонента Database Mail, используйте мастер настройки компонента Database Mail.  
  
 Эта хранимая процедура находится в базе данных **msdb** . Эта хранимая процедура запускает очередь компонента Database Mail, которая хранит запросы на исходящие сообщения и включает активацию компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для внешней программы.  
  
 Если очереди запущены, внешняя программа компонента Database Mail может обрабатывать сообщения. Эта процедура позволяет перезапустить очереди после остановки очередей с помощью хранимой процедуры **sysmail_stop_sp** .  
  
> [!NOTE]  
>  Эта хранимая процедура запускает только очереди для компонента Database Mail. Эта хранимая процедура не активирует доставку сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как запустить Database Mail в базе данных **msdb** . Пример предполагает, что компонент Database Mail активирован.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Параметр конфигурации сервера Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
