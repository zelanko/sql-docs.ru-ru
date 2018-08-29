---
title: sysmail_stop_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: 0d52e7f18373303673afc3e5ef67aeb91e094360
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021138"
---
# <a name="sysmailstopsp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Прекращает работу компонента Database Mail, останавливая работу объектов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], используемых внешней программой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Эта хранимая процедура находится в **msdb** базы данных.  
  
 Она останавливает обработку очереди компонента Database Mail, содержащей исходящие запросы, и выполняет деактивацию компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] для внешней программы.  
  
 Когда обработка очередей остановлена, внешняя программа, работающая с компонентом Database Mail, не обрабатывает сообщения. Эта хранимая процедура позволяет остановить работу компонента Database Mail для диагностики или обслуживания.  
  
 Для запуска компонента Database Mail, используйте **sysmail_start_sp**. Обратите внимание, что **sp_send_dbmail** продолжает принимать почты, когда [!INCLUDE[ssSB](../../includes/sssb-md.md)] остановки объектов.  
  
> [!NOTE]  
>  Эта хранимая процедура останавливает только обработку очередей компонента Database Mail. Эта хранимая процедура не приводит к деактивации доставки сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных. Эта системная процедура не отключает расширенные хранимые процедуры компонента Database Mail, т. е. не сокращает контактную зону. Чтобы отключить расширенные хранимые процедуры, см. в разделе [параметр Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) из **sp_configure** системной хранимой процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, остановка компонента Database Mail в **msdb** базы данных. Пример предполагает, что компонент Database Mail активирован.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
