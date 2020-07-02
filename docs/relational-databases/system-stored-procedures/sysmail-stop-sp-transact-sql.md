---
title: sysmail_stop_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6ed9d4a05759495090a35224e5aa5ef805e520f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783698"
---
# <a name="sysmail_stop_sp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Прекращает работу компонента Database Mail, останавливая работу объектов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], используемых внешней программой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>Аргументы  
 Отсутствуют  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура находится в базе данных **msdb** .  
  
 Она останавливает обработку очереди компонента Database Mail, содержащей исходящие запросы, и выполняет деактивацию компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для внешней программы.  
  
 Когда обработка очередей остановлена, внешняя программа, работающая с компонентом Database Mail, не обрабатывает сообщения. Эта хранимая процедура позволяет остановить работу компонента Database Mail для диагностики или обслуживания.  
  
 Чтобы запустить Database Mail, используйте **sysmail_start_sp**. Обратите внимание, что **sp_send_dbmail** по-прежнему принимает почту при [!INCLUDE[ssSB](../../includes/sssb-md.md)] остановке объектов.  
  
> [!NOTE]  
>  Эта хранимая процедура останавливает только обработку очередей компонента Database Mail. Эта хранимая процедура не приводит к деактивации доставки сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных. Эта системная процедура не отключает расширенные хранимые процедуры компонента Database Mail, т. е. не сокращает контактную зону. Сведения об отключении расширенных хранимых процедур см. в описании [параметра Database Mail XPS](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) системной хранимой процедуры **sp_configure** .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показана остановка Database Mail в базе данных **msdb** . Пример предполагает, что компонент Database Mail активирован.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
