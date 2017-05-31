---
title: "Класс событий Broker:Remote Message Ack | Документация Майкрософт"
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
- Broker:Remote Message Ack event class
ms.assetid: 3d67efe1-74b4-4633-b029-c6e05b19f4dc
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 747d421d4a9e6a86295ce843aa6c2b943bf006cf
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="brokerremote-message-ack-event-class"></a>Broker:Remote Message Ack, класс событий
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Broker:Remote Message Ack** , когда компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] отправляет или получает подтверждение сообщения.  
  
## <a name="brokerremote-message-ack-event-class-data-columns"></a>Столбцы данных класса событий Broker:Remote Message Ack  
  
|Столбец данных|Тип|Описание|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**BigintData1**|**bigint**|Последовательный номер сообщения, содержащего подтверждение.|52|Нет|  
|**BigintData2**|**bigint**|Последовательный номер подтверждаемого сообщения.|53|Нет|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанный в инструкции USE *database* . Если инструкция USE *database* не выполнялась для этого экземпляра, тогда это идентификатор базы данных по умолчанию. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**EventClass**|**int**|Тип захваченного класса событий. Всегда **149** или **Broker:Message Ack**.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|Нет|  
|**EventSubClass**|**nvarchar**|Тип подкласса события, предоставляющий дополнительные сведения о каждом классе событий. Этот столбец может содержать следующие значения.<br /><br /> **Message With Acknowledgement Sent**:<br />                    [!INCLUDE[ssSB](../../includes/sssb-md.md)] отправил подтверждение как часть обычного последовательного сообщения.<br /><br /> **Acknowledgement Sent**:<br />                    [!INCLUDE[ssSB](../../includes/sssb-md.md)] отправил подтверждение вне обычного последовательного сообщения.<br /><br /> **Message With Acknowledgement Received**:<br />                  [!INCLUDE[ssSB](../../includes/sssb-md.md)] получил подтверждение как часть обычного последовательного сообщения.<br /><br /> **Acknowledgement Received**:<br />                  [!INCLUDE[ssSB](../../includes/sssb-md.md)] получил подтверждение вне обычного последовательного сообщения.|21|Да|  
|**GUID**|**uniqueidentifier**|Идентификатор диалога. Этот идентификатор передается в составе сообщения и является общим для обоих участников диалога.|54|Нет|  
|**HonorBrokerPriority**|**Int**|Текущее значение параметра базы данных HONOR_BROKER_PRIORITY: 0 — отключено, 1 — включено.|32|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IntegerData**|**int**|Номер фрагмента сообщения, содержащего подтверждение.|25|Нет|  
|**IntegerData2**|**int**|Номер фрагмента подтверждаемого сообщения.|55|Нет|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе.<br /><br /> 0 = пользовательский процесс<br /><br /> 1 = системный процесс|60|Нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**Приоритет**|**int**|Уровень приоритета диалога.|5|Да|  
|**RoleName**|**nvarchar**|Роль экземпляра, подтвердившего сообщение. Это либо **initiator** , либо **target**.|38|Нет|  
|**ServerName**|**nvarchar**|Имя отслеживаемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|26|Нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если доступно.|14|Да|  
|**StarvationElevation**|**int**|Сообщение было отправлено с более высоким приоритетом, чем приоритет, настроенный для диалога: 0 — нет, 1 — да.|33|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Нет|  
  
  
