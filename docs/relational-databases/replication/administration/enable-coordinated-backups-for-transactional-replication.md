---
title: Включение скоординированного резервного копирования (транзакции)
description: Узнайте, как включить в базе данных распространителя функции скоординированного резервного копирования, при которых журнал транзакций в базе данных публикации репликации транзакций не подвергается усечению до получения резервных копий транзакций, переданных распространителю.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96fa2e96021f0390fcc1cf15eb3aba2fd6b55e42
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322059"
---
# <a name="enable-coordinated-backups-for-transactional-replication"></a>Включение скоординированного резервного копирования для репликации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При подготовке базы данных к репликации транзакций можно указать, что перед отправкой в базу данных распространителя со всех транзакций должны быть сняты резервные копии. Кроме того, существует возможность включения в базе данных распространителя функции скоординированного резервного копирования, при которой журнал транзакций в базе данных публикации не подвергается усечению до получения резервных копий транзакций, переданных распространителю. Дополнительные сведения см. в статье [Стратегии резервного копирования и восстановления из копии репликации моментальных снимков и репликации транзакций](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>Включение функции скоординированного резервного копирования для базы данных, опубликованной с использованием репликации транзакций  
  
1.  В издателе с помощью функции[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) получите значение свойства **IsSyncWithBackup** для базы данных издателя. Если функция возвратила значение **1**, то это означает, что скоординированное резервное копирование опубликованной базы данных уже включено.  
  
2.  Если функция, выполненная на шаге 1, возвратила значение **0**, выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) в базе данных издателя в издателе. Укажите значение **sync with backup** в параметре **\@optname** и значение **true** в параметре **\@value**.  
  
    > [!NOTE]  
    >  Если значение параметра **sync with backup** заменить на **false**, то точка усечения базы данных публикации будет обновлена после запуска агента чтения журнала или по истечении определенного интервала в случае, если агент чтения журнала выполняется постоянно. Максимальное значение интервала управляется параметром агента **–MessageInterval** , значение которого по умолчанию составляет 30 секунд.  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>Включение скоординированного резервного копирования базы данных распространителя  
  
1.  На распространителе с помощью функции[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) получите значение свойства **IsSyncWithBackup** для базы данных распространителя. Если функция возвратила значение **1**, то это означает, что скоординированное резервное копирование базы данных распространителя уже включено.  
  
2.  Если функция, выполненная на шаге 1, возвратила значение **0**, выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) в базе данных распространителя на распространителе. Укажите значение **sync with backup** в параметре **\@optname** и значение **true** в параметре **\@value**.  
  
### <a name="to-disable-coordinated-backups"></a>Отключение скоординированного резервного копирования  
  
1.  В издателе в базе данных публикации или в распространителе в базе данных распространителя выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md). Укажите значение **sync with backup** в параметре **\@optname** и значение **false** в параметре **\@value**.  
  
  
