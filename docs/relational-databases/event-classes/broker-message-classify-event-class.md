---
title: Класс событий Broker:Message Classify | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5e6c3eb4997cd89bae19a231e808cb4699528e97
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632442"
---
# <a name="brokermessage-classify-event-class"></a>класс событий Broker:Message Classify
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает событие класса **Broker:Message Classify** , когда компонент Service Broker определяет маршрут для сообщения.  
  
## <a name="brokermessage-classify-event-class-data-columns"></a>Столбцы данных класса событий Broker:Message Classify  
  
|Столбец данных|Тип данных|Описание|Номер столбца|Фильтруемый|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**EventClass**|**int**|Тип захваченного класса событий. Для **Broker:Message Classify** всегда равен **141**.|27|нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|нет|  
|**EventSubClass**|**nvarchar**|Тип подкласса событий, предоставляющий дополнительные сведения о каждом классе события. Этот столбец может содержать следующие значения.<br /><br /> **Local**: выбранный маршрут имеет адрес LOCAL.<br /><br /> **Remote**: выбранный маршрут имеет адрес, отличный от LOCAL.<br /><br /> **Delayed**: сообщение отложено либо из-за того, что переадресация выключена, либо из-за отсутствия подходящего маршрута.|21|Да|  
|**FileName**|**nvarchar**|Имя службы, которой направлено сообщение.|36|нет|  
|**GUID**|**uniqueidentifier**|Идентификатор диалога. Этот идентификатор передается в составе сообщения и является общим для обоих участников диалога.|54|нет|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**OwnerName**|**nvarchar**|Идентификатор посредника, которому направлено сообщение.|37|нет|  
|**RoleName**|**nvarchar**|Показывает, было ли сообщение получено из сети или порождено данным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|38|нет|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**Start Time**|**datetime**|Время начала события, если доступно.|14|Да|  
|**TargetUserName**|**nvarchar**|Сетевой адрес посредника следующего шага.|39|нет|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|нет|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
