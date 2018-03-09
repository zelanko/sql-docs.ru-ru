---
title: "Инициализация нового узла (одноранговая репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.p2pwizard.init.f1
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
caps.latest.revision: "20"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9acd541075532d1ed56794053ad4c85e64bd9862
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="new-peer-initialization-peer-to-peer-replication"></a>Инициализация нового узла (одноранговая репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Для указания метода инициализации одноранговых баз данных служит страница **Инициализация нового узла**. (Узлы необходимо инициализировать перед завершением этого мастера). Узлы инициализируются вручную или с помощью **инициализации при помощи резервной копии** , предоставляемой репликацией транзакций. (Одноранговая репликация транзакций не поддерживает инициализацию узлов с помощью моментальных снимков). Если разные узлы необходимо инициализировать разными методами, нужно добавлять узлы по отдельности, запустив мастер несколько раз.  
  
## <a name="options"></a>Параметры  
 **Укажите способ инициализации новых одноранговых баз данных**  
 Схема и данные для всех опубликованных объектов должны присутствовать на каждом узле. Выберите один из следующих вариантов.  
  
-   Выберите первый вариант, если схема для опубликованных объектов была создана вручную или восстановлена резервная копия, а данные в первой базе данных публикации не изменялись со времени резервного копирования. При создании схемы вручную необходимо обеспечить присутствие всех необходимых данных на каждом узле. Этот режим соответствует значению **только поддержка репликации** для свойства подписки **sync_type**.  
  
-   Выберите второй вариант, если была восстановлена резервная копия и данные в первой базе данных публикации изменились со времени резервного копирования. Теперь репликация должна доставить из первой базы данных публикации те изменения, которые не были включены в резервную копию. Этот режим соответствует значению **инициализации при помощи резервной копии** для свойства подписки **sync_type**.  
  
     Если публикация разрешена для одноранговой репликации, то свойство публикации **allow_initialize_from_backup** получает значение. Репликация немедленно начинает отслеживать изменения в первой базе данных публикации. Поэтому эти изменения можно доставить в восстановленную базу данных на одном или нескольких узлах при выборе **инициализации при помощи резервной копии** . Нажмите кнопку **Обзор** для поиска используемой резервной копии, и репликация прочитает регистрационный номер транзакции в журнале (LSN) из этой резервной копии. Все изменения в первой базе данных публикации с большими номерами LSN будут перенесены на каждый узел.  
  
     Этот параметр может быть недоступен, если создается или добавляется топология, включающая [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. В следующей таблице показано, доступен ли этот параметр при добавлении узла к существующей топологии.  
  
    |Новый узел|Первый узел|Дополнительные узлы|Параметр|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Выключено|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|None|Выключено|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Выключено|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|None|Активировано|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|None|Активировано|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Активировано|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|None|Активировано|  
  
## <a name="see-also"></a>См. также:  
 [Администрирование одноранговой топологии (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
