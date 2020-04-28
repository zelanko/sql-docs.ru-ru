---
title: sp_replicationdboption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c0837db9666ab6b49aee30b81b5585cbf5d5ee0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74056773"
---
# <a name="sp_replicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Устанавливает аргументы репликации указанной базы данных. Эта хранимая процедура выполняется на издателе или подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'`База данных, для которой задается параметр базы данных репликации. Аргумент *db_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @optname = ] 'optname'`Параметр базы данных репликации для включения или отключения. *optname* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Публикация слиянием**|База данных может использоваться для публикации слиянием.|  
|**отменить**|База данных может использоваться для других типов публикаций.|  
|**subscribe**|База данных является базой данных подписки.|  
|**sync with backup**|База данных доступна для скоординированного создания резервных копий. Дополнительные сведения см. в разделе [Включение координированных резервных копий для репликации транзакций &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md).|  
  
`[ @value = ] 'value'`Указывает, следует ли включить или отключить данный параметр базы данных репликации. **аргумент** *value* имеет тип sysname и может принимать **значение true** или **false**. Если это значение равно **false** и *optname* является **публикацией слиянием**, то подписки на опубликованную базу данных слияния также удаляются.  
  
`[ @ignore_distributor = ] ignore_distributor`Указывает, выполняется ли эта хранимая процедура без соединения с распространителем. *ignore_distributor* имеет **бит**, значение по умолчанию **0**, означающее, что распространитель должен быть подключен к и обновлен с новым состоянием базы данных публикации. Значение **1** должно быть указано, только если распространитель недоступен, а **sp_replicationdboption** используется для отключения публикации.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_replicationdboption** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Эта процедура создает или удаляет определенные системные таблицы репликации, учетные записи безопасности и так далее в зависимости от указанного аргумента. Задает соответствующее **is_published** (репликация трансакатионал или моментального снимка), **is_merge_published** (репликация слиянием) или **is_distributor** бит в системной таблице **master. databases** и создает необходимые системные таблицы.  
  
 Для отключения публикации база данных публикации должна находиться в режиме «в сети». Если для базы данных публикации существует моментальный снимок, он должен быть удален перед отключением публикации. Моментальный снимок базы данных доступен только для чтения в виде копии базы данных вне сети и не относится к моментальному снимку репликации. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_replicationdboption**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Удаление публикации](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Отключение публикации и распространения](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
