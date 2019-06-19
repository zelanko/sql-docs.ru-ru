---
title: Включение скоординированного резервного копирования для репликации транзакций (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 5055305259715c323e1f6cb26fc3428879acfddb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186981"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a>включить скоординированное создание резервных копий для репликации транзакций (программирование репликации на языке Transact-SQL)
  При подготовке базы данных к репликации транзакций можно указать, что перед отправкой в базу данных распространителя со всех транзакций должны быть сняты резервные копии. Кроме того, существует возможность включения в базе данных распространителя функции скоординированного резервного копирования, при которой журнал транзакций в базе данных публикации не подвергается усечению до получения резервных копий транзакций, переданных распространителю. Дополнительные сведения см. в статье [Стратегии резервного копирования и восстановления из копии репликации моментальных снимков и репликации транзакций](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>Включение функции скоординированного резервного копирования для базы данных, опубликованной с использованием репликации транзакций  
  
1.  В издателе с помощью функции[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) получите значение свойства **IsSyncWithBackup** для базы данных издателя. Если функция возвратила значение **1**, то это означает, что скоординированное резервное копирование опубликованной базы данных уже включено.  
  
2.  Если функция, выполненная на шаге 1, возвратила значение **0**, выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) в базе данных издателя в издателе. Укажите значение **sync with backup** для аргумента **@optname** и значение **true** для аргумента **@value** .  
  
    > [!NOTE]  
    >  Если значение параметра **sync with backup** заменить на **false**, то точка усечения базы данных публикации будет обновлена после запуска агента чтения журнала или по истечении определенного интервала в случае, если агент чтения журнала выполняется постоянно. Максимальное значение интервала управляется параметром агента **-MessageInterval**, значение которого по умолчанию составляет 30 секунд.  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>Включение скоординированного резервного копирования базы данных распространителя  
  
1.  На распространителе с помощью функции[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) получите значение свойства **IsSyncWithBackup** для базы данных распространителя. Если функция возвратила значение **1**, то это означает, что скоординированное резервное копирование базы данных распространителя уже включено.  
  
2.  Если функция, выполненная на шаге 1, возвратила значение **0**, выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) в базе данных распространителя на распространителе. Укажите значение **sync with backup** для аргумента **@optname** , а в параметре **true** для аргумента **@value** .  
  
### <a name="to-disable-coordinated-backups"></a>Отключение скоординированного резервного копирования  
  
1.  В издателе в базе данных публикации или в распространителе в базе данных распространителя выполните хранимую процедуру [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Укажите значение **sync with backup** для аргумента **@optname** , а в параметре **false** для аргумента **@value** .  
  
  
