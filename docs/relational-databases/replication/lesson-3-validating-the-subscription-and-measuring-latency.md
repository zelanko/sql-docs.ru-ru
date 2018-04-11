---
title: Занятие 3. Проверка подписки и измерение задержки | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ad3fadb0017628fa54a102366f132bbc72b9cfb
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>Занятие 3. Проверка подписки и измерение задержки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
На этом занятии изучаются трассировочные токены для проверки реплицируемых для подписчика изменений и определения задержки, т.е. времени, когда изменение, внесенное на стороне издателя, должно перейти на сторону подписчика. Приступать к этому занятию нужно только по завершении предыдущего: [Занятие 2. Создание подписки на публикацию транзакций](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>Вставка трассировочного токена и просмотр сведений о токене  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], разверните узел сервера, щелкните правой кнопкой мыши папку **Репликация** и выберите пункт **Запустить монитор репликации**.  
  
    Запустится монитор репликации.  
  
2.  Раскройте группу издателей на левой панели, затем экземпляр издателя и выберите публикацию **AdvWorksProductTrans** .  
  
3.  Щелкните вкладку **Трассировочные токены** .  
  
4.  Выберите команду **Вставить трассировочный маркер**.  
  
5.  Просмотрите затраченное время для трассировочного маркера в следующих столбцах: **От издателя к распространителю**, **От распространителя к подписчику**, **Общая задержка**. Значение **Ожидание** указывает на то, что токен еще не достиг указанной точки.  
  
## <a name="next-steps"></a>Next Steps  
На этом занятии показывается, как использовать трассировочные токены для проверки изменений, реплицируемых от издателя подписчику. Кроме того, показывается, как вставлять, обновлять и удалять данные из таблицы **Product** на стороне издателя и строить запрос к таблице **Product** на стороне подписчика для проверки изменений после репликации.  
  
На этом учебник «Репликация данных между постоянно соединенными серверами» завершается. Похожий учебник, использующий репликацию слиянием, см. в разделе [Tutorial: Replicating Data with Mobile Clients](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md).  
  
## <a name="see-also"></a>См. также:  
[Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
  
