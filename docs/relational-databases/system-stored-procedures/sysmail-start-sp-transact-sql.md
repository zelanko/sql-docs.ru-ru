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
manager: craigg
ms.openlocfilehash: 877fa31954cb0bf7255d831475c875fb43d002b8
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210013"
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
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
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Компонент Database Mail не включен, или не установлен, или не включен в установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы включить и установить объекты компонента Database Mail, используйте мастер настройки компонента Database Mail.  
  
 Эта хранимая процедура находится в **msdb** базы данных. Эта хранимая процедура запускает очередь компонента Database Mail, которая хранит запросы на исходящие сообщения и включает активацию компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для внешней программы.  
  
 Если очереди запущены, внешняя программа компонента Database Mail может обрабатывать сообщения. Эта процедура позволяет перезапускать очереди, после они были остановлены с **sysmail_stop_sp** хранимой процедуры.  
  
> [!NOTE]  
>  Эта хранимая процедура запускает только очереди для компонента Database Mail. Эта хранимая процедура не активирует доставку сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, начиная с версии компонента Database Mail **msdb** базы данных. Пример предполагает, что компонент Database Mail активирован.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Параметр конфигурации сервера Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
