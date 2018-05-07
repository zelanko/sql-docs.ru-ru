---
title: MSpublications (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ab3987fddb89b3ec037d191be0d640922675428e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublications** содержит по одной строке для каждой публикации, которая реплицируется издателем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**Публикации**|**sysname**|Имя публикации.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = публикация транзакций.<br /><br /> **1** = моментальный снимок.<br /><br /> **2** = публикация слиянием.|  
|**thirdparty_flag**|**бит**|Указывает, является ли публикация [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **1** = источник данных, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**independent_agent**|**бит**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**immediate_sync**|**бит**|Указывает, создаются ли повторно файлы синхронизации при каждом запуске агента моментальных снимков.|  
|**allow_push**|**бит**|Указывает, могут ли быть созданы для данной публикации принудительные подписки.|  
|**allow_pull**|**бит**|Указывает, могут ли быть созданы для данной публикации подписки по запросу.|  
|**allow_anonymous**|**бит**|Указывает, могут ли быть созданы для данной публикации анонимные подписки.|  
|**Описание**|**nvarchar(255)**|Описание публикации.|  
|**vendor_name**|**Nvarchar(100)**|Имя поставщика, если издатель не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.|  
|**Хранения**|**int**|Срок хранения публикации в часах.|  
|**sync_method**|**int**|Метод синхронизации.<br /><br /> **0** = native (производит массовое копирование вывода всех таблиц).<br /><br /> **1** = символ (формирует символьное массовое копирование вывода всех таблиц).<br /><br /> **3** = одновременный (производит массовое копирование вывода всех таблиц, но не блокирует таблицы во время моментального снимка).<br /><br /> **4** = Concurrent_c (Одновременный символьный режим массовое копирование вывода всех таблиц, но не блокирует таблицы во время моментального снимка)<br /><br /> Значения **3** и **4** доступны для репликации транзакций и репликации слиянием, но не для репликации моментальных снимков.|  
|**allow_subscription_copy**|**бит**|Разрешает или запрещает возможность копирования баз данных подписки, подписанных на эту публикацию. **0** означает, что копирование отключено, и **1** означает он включен.|  
|**thirdparty_options**|**int**|Указывает, является ли отображение публикации в папке «репликация» в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подавляется:<br /><br /> **0** = отображает разнородные публикации в папке «репликация» в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> **1** = подавляет отображение разнородных публикаций в папке «репликация» в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**allow_queued_tran**|**бит**|Определяет, позволяет ли обновление публикация посредством очередей:<br /><br /> **0 =** публикация ставится в очередь.<br /><br /> **1** = публикация ставится в очередь.|  
|**Параметры**|**int**|Сведения для данного выпуска отсутствуют.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
