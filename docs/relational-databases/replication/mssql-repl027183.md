---
title: MSSQL_REPL027183 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b329123e3b2df0b2fc820539b439725b0c4ee4c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020177"
---
# <a name="mssqlrepl027183"></a>MSSQL_REPL027183
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|27183|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Процессу слияния не удалось перечислить изменения в статьях с параметризованными фильтрами строк. Если эта ошибка продолжает возникать, увеличьте тайм-аут запроса для этого процесса, уменьшите срок хранения публикации и оптимизируйте индексы по опубликованным таблицам.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка появляется, если возникает тайм-аут агента слияния во время обработки изменений в фильтруемой публикации. Тайм-аут может быть вызван одной из следующих причин:  
  
-   Не используется оптимизация предварительно вычисляемых секций.  
  
-   Для фильтрации используется фрагментация индекса столбцов.  
  
-   Большие объединенные таблицы метаданных, например **MSmerge_tombstone**, **MSmerge_contents**и **MSmerge_genhistory**.  
  
-   Фильтруемые таблицы, не соединенные уникальным ключом, и фильтры соединения, использующие большое количество таблиц.  
  
## <a name="user-action"></a>Действие пользователя  
 Способы устранения проблемы.  
  
-   Увеличьте для агента слияния значение параметра **-QueryTimeOut** , чтобы разрешить продолжение обработки, пока будут устраняться основные причины, вызывающие эту ошибку. Параметры агента могут задаваться в профилях агента или в командной строке. Дополнительные сведения см. в разделе:  
  
    -   [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Просмотр и изменение параметров командной строки агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   По возможности используйте оптимизацию предварительно вычисляемых секций. Эта оптимизация используется по умолчанию в случае выполнения ряда требований к публикации. Дополнительные сведения об этих требованиях см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md). Если публикация не отвечает этим требованиям, рассмотрите возможность повторной разработки публикации.  
  
-   Укажите наименьшее возможное значение срока хранения данной публикации, потому что репликация не может выполнять очистку метаданных в базах данных публикации и подписок, пока не истечет срок хранения. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   В процессе обслуживания репликации слиянием иногда проверяйте увеличение размера системных таблиц, связанных с репликацией слиянием: **MSmerge_contents**, **MSmerge_genhistory**, **MSmerge_tombstone**, **MSmerge_current_partition_mappings** и **MSmerge_past_partition_mappings**. Время от времени проводите повторную индексацию этих таблиц. Дополнительные сведения см. в статье [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Убедитесь в том, что столбцы, используемые для фильтрации, надлежащим образом проиндексированы, и при необходимости перестройте такие индексы заново. Дополнительные сведения см. в статье [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Для фильтров соединения, основанных на уникальных столбцах, задайте свойство **join_unique_key** . Дополнительные сведения см. в статье [Join Filters](../../relational-databases/replication/merge/join-filters.md).  
  
-   Ограничьте число таблиц, входящих в иерархию фильтра соединения. При создании фильтров соединения из пяти и более таблиц рассмотрите другие решения: не фильтруйте маленькие таблицы, таблицы, которые не изменяются или служат в основном таблицами подстановки. Используйте фильтры соединения только между теми таблицами, которые должны быть секционированы среди подписок.  
  
-   Уменьшите количество изменений в фильтруемых таблицах между синхронизациями или чаще запускайте агент слияния. Дополнительные сведения о настройке расписаний синхронизации см. в разделе [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
