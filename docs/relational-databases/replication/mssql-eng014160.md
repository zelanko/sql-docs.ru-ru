---
title: MSSQL_ENG014160 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a25abaee561ea74bd29dff369a8c4ec5ac516fee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746262"
---
# <a name="mssqleng014160"></a>MSSQL_ENG014160
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14160|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Срок действия подписки на эту публикацию истек у одного или нескольких подписчиков.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит приближение истечения срока действия подписки. Срок действия подписок может закончиться, если они не будут синхронизированы в течение определенного *срока хранения*. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Решение проблемы зависит от причины выдачи предупреждения:  
  
-   Если превышено пороговое значение, но срок действия подписки еще не истек, синхронизируйте подписку. Дополнительные сведения см. в разделе [Синхронизация данных](../../relational-databases/replication/synchronize-data.md).  
  
-   Если агент работал, но неправильно реплицировал изменения, это могло стать причиной истечения срока действия подписки. В случае репликации транзакций удостоверьтесь, что работают агент распространителя и агент чтения журнала. В случае репликации слиянием удостоверьтесь, что работает агент слияния. Дополнительные сведения о запуске этих агентов см. в статьях [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Если срок действия подписки истек, ее необходимо либо повторно инициализировать, либо удалить и создать повторно. Это зависит от типа подписки и того, как давно истек ее срок действия. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
