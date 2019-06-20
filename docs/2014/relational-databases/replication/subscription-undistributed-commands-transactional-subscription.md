---
title: Подписка, Нераспространенные команды (подписка на публикацию транзакций, SQL Server 2005 и более поздние версии) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a1f957c417c5c63766dfbffa923edd6935d1eb5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151483"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a>Подписка, нераспространенные команды (подписка на публикацию транзакций, SQL Server 2005 и более поздние версии)
  На вкладке **Нераспространенные команды** отображаются сведения о количестве команд в базе данных распространителя, которые не были доставлены выбранному подписчику, и приблизительное время для доставки этих команд. Дополнительные сведения о просмотре этих команд в базе данных распространителя см. в статье [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).  
  
## <a name="options"></a>Параметры  
 **Число команд в базе данных распространителя, которые ожидают применения к этому подписчику.**  
 Количество команд в базе данных распространителя, которые не были доставлены выбранному подписчику. Команда состоит из одной инструкции языка обработки данных (DML) или одной инструкции языка определения данных (DDL) языка Transact-SQL.  
  
 **Расчетное время применения этих команд, вычисленное по результатам предыдущего выполнения.**  
 Примерное количество времени, необходимое для доставки команд на подписчик. Если это значение превышает количество времени, требуемое для создания и применения моментального снимка на подписчике, рассмотрите возможность повторной инициализации подписчика. Дополнительные сведения см. в статье [Повторная инициализация подписок](reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>См. также  
 [Запуск монитора репликации](monitor/start-the-replication-monitor.md)   
 [Наблюдение за производительностью с помощью монитора репликации](monitor/monitor-performance-with-replication-monitor.md)   
 [Наблюдение за репликацией](monitoring-replication.md)  
  
  
