---
title: MSSQL_ENG014151 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 497e36c9abb5e0429e169de26f5dcfcc7944a0de
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168351"
---
# <a name="mssqleng014151"></a>MSSQL_ENG014151
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14151|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Репликация-%s: ошибка агента %s. %s|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка возникает в случае сбоя любого агента репликации. Текст в конце сообщения зависит от контекста сбоя.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта ошибка может возникать в нескольких ситуациях; в зависимости от сложившихся обстоятельств используйте следующие подходы:  
  
-   Перезапустите агент, сбой которого произошел, и посмотрите, будет ли он теперь работать без сбоев. Дополнительные сведения см. в статьях и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](concepts/replication-agent-executables-concepts.md).  
  
-   Проверьте журнал агента и журнал заданий на наличие других ошибок, возникших приблизительно в то же время. Сведения о просмотре состояния агента и подробных сведений об ошибке в мониторе репликации см. в следующих разделах:  
  
    -   Дополнительные сведения об агенте моментальных снимков, агенте чтения журнала и агенте чтения очереди вы найдете в статье [Просмотр сведений и выполнение задач для агентов, связанных с публикацией (монитор репликации)](monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Дополнительные сведения об агенте распределения и агенте слияния вы найдете в статье [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Проверьте функционирование базовых соединений между компьютерами, к которым обращается агент, а затем подключитесь к каждому из этих компьютеров, используя программу, такую как [sqlcmd Utility](../../tools/sqlcmd-utility.md). При подключении используйте ту же учетную запись, под которой агент устанавливает соединения. Дополнительные сведения о правах доступа, необходимых учетной записи каждого агента, см. в разделе [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
-   Если ошибка возникает при создании или применении моментального снимка, проверьте файлы в каталоге моментальных снимков на наличие ошибок.  
  
-   Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## <a name="see-also"></a>См. также  
 [Администрирование агента репликации](agents/replication-agent-administration.md)   
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [Агент распространения репликации](agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
