---
title: MSSQL_ENG014151 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f292841c227db26f1c518b2eaef896f7ce3570c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191458"
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
  
-   Проверьте журнал агента и журнал заданий на наличие других ошибок, возникших приблизительно в то же время. Сведения о просмотре состояния агента и сведений об ошибках в мониторе репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
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
 [Агент моментальных снимков репликации](agents/replication-snapshot-agent.md)  
  
  
