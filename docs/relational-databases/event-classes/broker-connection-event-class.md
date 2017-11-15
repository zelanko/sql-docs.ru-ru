---
title: "Класс событий Broker:Connection | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Broker:Connection event class
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2f07fc7b5e182a223bbdecec27d2081662958558
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="brokerconnection-event-class"></a>Broker:Connection, класс событий
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Broker:Connection** для уведомления о состоянии транспортного соединения, управляемого компонентом Service Broker.  
  
## <a name="brokerconnection-event-class-data-columns"></a>Столбцы данных класса событий Broker:Connection  
  
|Столбец данных|Тип|Описание|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database*не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию **DB_ID** .|3|Да|  
|**Ошибка**|**int**|Идентификационный номер сообщения в представлении **sys.messages** для текста в событии. В случае ошибки в данном событии этот номер является номером ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|31|Нет|  
|**EventClass**|**int**|Тип захваченного класса событий. Всегда равен **138** для класса событий **Broker:Connection**.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|Нет|  
|**EventSubClass**|**nvarchar**|Состояние данного соединения. Для этого события производным классом является одно из следующих значений.<br /><br /> <br /><br /> **Соединение**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инициализирует транспортное соединение.<br /><br /> **Соединен**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установил транспортное соединение.<br /><br /> **Подключение не удалось**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : не удалось установить транспортное соединение.<br /><br /> **Закрытие**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывает транспортное соединение.<br /><br /> **Закрыто**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрыл транспортное соединение.<br /><br /> **Принято**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принял транспортное соединение от другого экземпляра.<br /><br /> **Ошибка ввода-вывода при отправке**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил ошибку транспортного соединения во время отправки сообщения.<br /><br /> **Ошибка ввода-вывода при получении**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил ошибку транспортного соединения во время получения сообщения.|21|Да|  
|**GUID**|**uniqueidentifier**|Идентификатор конечной точки данного соединения.|54|Нет|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию **HOST_NAME** .|8|Да|  
|**IntegerData**|**int**|Количество закрытий данного соединения.|25|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе.<br /><br /> 0 = пользовательский процесс<br /><br /> 1 = системный процесс|60|Нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ObjectName**|**nvarchar**|Дескриптор диалога.|34|Нет|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|Нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если доступно.|14|Да|  
|**TextData**|**ntext**|Текст сообщения об ошибке, относящейся к этому событию. Для событий, не формирующих сообщения об ошибке, данное поле остается незаполненным. Сообщение об ошибке может быть либо сообщением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо сообщением Windows.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Нет|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
