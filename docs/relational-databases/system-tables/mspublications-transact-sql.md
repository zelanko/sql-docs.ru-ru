---
title: MSpublications (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c576bd5ce66661eb601984638c0608ae2eef8f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732622"
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublications** таблица содержит по одной строке для каждой публикации, который реплицируется с издателя. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = публикация транзакций.<br /><br /> **1** = моментальный снимок.<br /><br /> **2** = публикация слиянием.|  
|**thirdparty_flag**|**bit**|Указывает, является ли публикацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **1** = источник данных, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**immediate_sync**|**bit**|Указывает, создаются ли повторно файлы синхронизации при каждом запуске агента моментальных снимков.|  
|**allow_push**|**bit**|Указывает, могут ли быть созданы для данной публикации принудительные подписки.|  
|**allow_pull**|**bit**|Указывает, могут ли быть созданы для данной публикации подписки по запросу.|  
|**allow_anonymous**|**bit**|Указывает, могут ли быть созданы для данной публикации анонимные подписки.|  
|**Описание**|**nvarchar(255)**|Описание публикации.|  
|**vendor_name**|**Nvarchar(100)**|Имя поставщика, если издатель не является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.|  
|**хранение**|**int**|Срок хранения публикации в часах.|  
|**sync_method**|**int**|Метод синхронизации.<br /><br /> **0** — собственная (производит массовое копирование вывода всех таблиц).<br /><br /> **1** = символ (порождает символьный; производит массовое копирование вывода всех таблиц).<br /><br /> **3** = одновременный (производит массовое копирование вывода всех таблиц, но не блокирует таблицы во время создания моментального снимка).<br /><br /> **4** = Concurrent_c (Одновременный символьный; производит массовое копирование вывода всех таблиц, но не блокирует таблицы во время создания моментального снимка)<br /><br /> Значения **3** и **4** доступны для репликации транзакций и репликации слиянием, но не для репликации моментальных снимков.|  
|**allow_subscription_copy**|**bit**|Разрешает или запрещает возможность копирования баз данных подписки, подписанных на эту публикацию. **0** означает, что копирование отключен, и **1** означает, что он включен.|  
|**thirdparty_options**|**int**|Указывает ли отображение публикации в папке репликаций [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подавляется:<br /><br /> **0** = отображает разнородные публикации в папке репликаций [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> **1** = подавляет отображение разнородных публикаций в папке репликации в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**allow_queued_tran**|**bit**|Определяет, позволяет ли обновление публикация посредством очередей:<br /><br /> **0 =** публикации, не использующих очереди.<br /><br /> **1** = публикация ставится в очередь.|  
|**Параметры**|**int**|Сведения для данного выпуска отсутствуют.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
