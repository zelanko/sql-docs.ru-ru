---
title: MSSQL_ENG021798 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 51cf4acc8ed270c8302137fe5050c06cb35e91ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63023535"
---
# <a name="mssql_eng021798"></a>MSSQL_ENG021798
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21798|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Перед продолжением необходимо добавить задание агента '%s' с помощью '%s'. См. документацию по "%s".»|  
  
## <a name="explanation"></a>Объяснение  
 Для создания публикации необходимо быть членом предопределенной роли сервера **sysadmin** на издателе или членом предопределенной роли базы данных **db_owner** в базе данных публикации. Если вы являетесь членом роли базы данных **db_owner** , эта ошибка возникает в следующих случаях:  
  
-   Выполняются скрипты из [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Модель безопасности в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]изменилась, поэтому эти скрипты необходимо обновить.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением процедуры [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql). Это относится ко всем публикациям транзакций.  
  
-   Хранимая процедура **sp_addpublication** выполняется перед выполнением процедуры [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql). Это относится к публикациям транзакций, для которых включены обновляемые посредством очередей подписки (значение TRUE для **@allow_queued_tran** параметра **sp_addpublication**).  
  
 Хранимые процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** создают задание агента и позволяют задать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. Для пользователей в роли **sysadmin** задания агентов создаются явно, если процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** не выполняются. Агент запускается в контексте учетной записи службы агентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на распространителе. Несмотря на то, что процедуры **sp_addlogreader_agent** и **sp_addqreader_agent** необязательны для пользователей в роли **sysadmin** , в целях обеспечения надлежащей безопасности рекомендуется задать отдельную учетную запись для агентов. Дополнительные сведения см. в статье [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что процедуры выполняются в правильном порядке. Дополнительные сведения см. в статьях [Создание публикации](publish/create-a-publication.md), обновление этих скриптов для включения хранимых процедур и параметров, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] необходимых для и более поздних версий. Дополнительные сведения см. в статье [Обновление скриптов репликации (программирование репликации на языке Transact-SQL)](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## <a name="see-also"></a>См. также:  
 [Ошибки и события ссылаются на &#40;&#41;репликации](errors-and-events-reference-replication.md)  
  
  
