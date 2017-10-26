---
title: "MSSQL_ENG021798 | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 526b6bd1e3e2a709bbe66ec2ee06d73637cf1027
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng021798"></a>MSSQL_ENG021798
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21798|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Перед продолжением необходимо добавить задание агента '%s' с помощью '%s'. См. документацию по "%s".»|  
  
## <a name="explanation"></a>Объяснение  
 Для создания публикации необходимо быть членом предопределенной роли сервера **sysadmin** на издателе или членом предопределенной роли базы данных **db_owner** в базе данных публикации. Если вы являетесь членом роли базы данных **db_owner** , эта ошибка возникает в следующих случаях:  
  
-   Выполняются скрипты из [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Модель безопасности в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]изменилась, поэтому эти скрипты необходимо обновить.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением процедуры [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Это относится ко всем публикациям транзакций.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением процедуры [sp_addqreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Это относится к публикациям транзакций, которые включены для подписок, обновляемых посредством очередей (значение TRUE для параметра **@allow_queued_tran** процедуры **sp_addpublication**).  
  
 Хранимые процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** создают задание агента и позволяют задать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. Для пользователей в роли **sysadmin** задания агентов создаются явно, если процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** не выполняются. Агент запускается в контексте учетной записи службы агентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на распространителе. Несмотря на то, что процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** необязательны для пользователей в роли **sysadmin** , в целях обеспечения надлежащей безопасности рекомендуется задать отдельную учетную запись для агентов. Дополнительные сведения см. в статье [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что процедуры выполняются в правильном порядке. Дополнительные сведения см. в статье [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md). При наличии скриптов репликации, оставшихся от предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обновите их, включив хранимые процедуры и параметры, необходимые для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий. Дополнительные сведения см. в статье [Обновление скриптов репликации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

