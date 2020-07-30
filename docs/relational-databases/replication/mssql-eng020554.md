---
title: MSSQL_ENG020554 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 7c88d0c4f17eed0c4a03d9bc037e2030ab539505
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363505"
---
# <a name="mssql_eng020554"></a>MSSQL_ENG020554
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20554|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Агент репликации не зарегистрировал сообщение о ходе выполнения в течение %ld минут. Это может указывать на то, что агент не отвечает, либо на высокую загрузку системы. Убедитесь, что записи реплицируются по назначению, а подключения к подписчику, издателю и распространителю все еще активны.|  
  
## <a name="explanation"></a>Объяснение  
 Задание **Проверка агентов репликации** выполняется с заданным интервалом (по умолчанию — 10 минут) для проверки состояния каждого агента репликации. Если с момента последней проверки контрольной суммы агентом в журнале не было сделано записей о сообщениях о выполнении, вызывается ошибка MSSQL_ENG020554. Предполагается, что агент записывает записи в журнал, даже если действий по репликации не производится. Но если агент репликации не реагирует, как положено, из этого не следует, что он был остановлен или что в его работе произошел сбой (если в работе агента произошел сбой, вызывается ошибка MSSQL_ENG020536).  
  
 К возникновению ошибки MSSQL_ENG020554 могут привести следующие причины:  
  
-   Агент занят.  
  
     Если агент слишком занят, чтобы ответить на опрос во время проверки, в отчете задания по проверке невозможно отметить, верно ли функционирует агент. Причиной занятости агента может быть репликация большого количества данных или неправильная конструкция или конфигурация приложения, в результате которой процессы выполняются очень долго.  
  
-   Агент не может вести записи в журнал на одном из компьютеров в данной топологии.  
  
     У всех агентов есть параметр **-LoginTimeOut** (по умолчанию задано 15 секунд), определяющий время, в течение которого агент предпринимает попытки входа на узел репликации (например, вход агента слияния на узел издателя). Если значение параметра **-LoginTimeOut** превышает интервал проверки агента репликации, проблема со входом может стать основной причиной ошибки: ошибка MSSQL_ENG020554 возникает прежде, чем агент может сформировать более конкретную ошибку.  
  
## <a name="user-action"></a>Действие пользователя  
 Необходимые действия зависят от причины возникновения ошибки.  
  
-   Во всех случаях возникновения данной ошибки:  
  
     Следует проверить подробные сведения об ошибке в мониторе репликации и перезапустить агент, если он был остановлен. В подробных сведениях об ошибке может содержаться дополнительная информация о причинах неверного поведения агента. Если агент до сих пор работает, останавливать и перезапускать его не следует, поскольку это может ухудшить проблему. Сведения о просмотре состояния агента и сведений об ошибках в мониторе репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).    
  
-   В случае частого возникновения данной ошибки из-за занятости агента:  
  
     Может потребоваться перепроектирование приложения таким образом, чтобы агенту требовалось меньше времени на обработку.  
  
     С помощью диалогового окна **Свойства задания** можно увеличить интервал проверки состояния агента. Сведения о доступе к этому диалоговому окну для заданий репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Агент не может вести записи в журнал на одном из компьютеров в данной топологии.  
  
     Рекомендуем устанавливать значение параметра **-LoginTimeOut** меньше, чем интервал проверки агента репликации. Иногда значение параметра **-LoginTimeOut** может быть больше, так как проблемы в сети могут привести к истечению времени ожидания входа в систему. Если значение параметра **-LoginTimeOut** меньше интервала проверки агента, в отчете репликации могут быть отмечены определенные ошибки, что позволяет решать проблемы входа в систему, вызванные разрешениями, проблемами в сети или другими неполадками. Параметры агента могут задаваться в профилях агента или в командной строке. Дополнительные сведения см. в разделе:  
  
    -   [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Просмотр и изменение параметров командной строки агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
