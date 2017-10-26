---
title: "Класс событий Broker:Message Classify | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2bf30690ffcd48df2aedf00bad6c1124c0a555f0
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="brokermessage-classify-event-class"></a>класс событий Broker:Message Classify
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает событие класса **Broker:Message Classify** , когда компонент Service Broker определяет маршрут для сообщения.  
  
## <a name="brokermessage-classify-event-class-data-columns"></a>Столбцы данных класса событий Broker:Message Classify  
  
|Столбец данных|Тип данных|Описание|Номер столбца|Фильтруемый|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**EventClass**|**int**|Тип захваченного класса событий. Для **Broker:Message Classify** всегда равен **141**.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|Нет|  
|**EventSubClass**|**nvarchar**|Тип подкласса событий, предоставляющий дополнительные сведения о каждом классе события. Этот столбец может содержать следующие значения.<br /><br /> **Local**: выбранный маршрут имеет адрес LOCAL.<br /><br /> **Remote**: выбранный маршрут имеет адрес, отличный от LOCAL.<br /><br /> **Delayed**: сообщение отложено либо из-за того, что переадресация выключена, либо из-за отсутствия подходящего маршрута.|21|Да|  
|**FileName**|**nvarchar**|Имя службы, которой направлено сообщение.|36|Нет|  
|**GUID**|**uniqueidentifier**|Идентификатор диалога. Этот идентификатор передается в составе сообщения и является общим для обоих участников диалога.|54|Нет|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**OwnerName**|**nvarchar**|Идентификатор посредника, которому направлено сообщение.|37|Нет|  
|**RoleName**|**nvarchar**|Показывает, было ли сообщение получено из сети или порождено данным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|38|Нет|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|Нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**Start Time**|**datetime**|Время начала события, если доступно.|14|Да|  
|**TargetUserName**|**nvarchar**|Сетевой адрес посредника следующего шага.|39|Нет|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Нет|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  

