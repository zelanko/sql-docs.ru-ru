---
title: Класс событий Database Mirroring Connection | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: b59dccc9-f40d-4c82-aa35-ac40acea86ff
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b5e73000ec424f6880440a8aa2a23659b92582b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672152"
---
# <a name="database-mirroring-connection-event-class"></a>Соединение зеркального отображения базы данных, класс событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Соединение для зеркального отображения базы данных** для уведомления о состоянии транспортного соединения, управляемого компонентом Database Mirroring.  
  
## <a name="database-mirroringconnection-event-class-data-columns"></a>Столбцы данных класса событий Database Mirroring:Connection  
  
|Столбец данных|Тип|Описание|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database*не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию **DB_ID** .|3|Да|  
|**Ошибка**|**int**|Идентификационный номер сообщения в представлении **sys.messages** для текста в событии. В случае ошибки в данном событии этот номер является номером ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|31|нет|  
|**EventClass**|**int**|Тип захваченного класса событий. Всегда **151** для **подключения к зеркально отображаемой базе данных**.|27|нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|нет|  
|**EventSubClass**|**nvarchar**|Состояние данного соединения. Для этого события подклассом является одно из следующих значений:<br /><br /> **Соединение**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инициализирует транспортное соединение.<br /><br /> **Соединен**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установил транспортное соединение.<br /><br /> **Подключение не удалось**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : не удалось установить транспортное соединение.<br /><br /> **Закрытие**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывает транспортное соединение.<br /><br /> **Закрыто**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрыл транспортное соединение.<br /><br /> **Принято**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принял транспортное соединение от другого экземпляра.<br /><br /> **Ошибка ввода-вывода при отправке**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил ошибку транспортного соединения во время отправки сообщения.<br /><br /> **Ошибка ввода-вывода при получении**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил ошибку транспортного соединения во время получения сообщения.|21|Да|  
|**GUID**|**uniqueidentifier**|Идентификатор конечной точки данного соединения.|54|нет|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию **HOST_NAME** .|8|Да|  
|**IntegerData**|**int**|Количество закрытий данного соединения.|25|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе.<br /><br /> 0 = пользовательский процесс<br /><br /> 1 = системный процесс|60|нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ObjectName**|**nvarchar**|Дескриптор диалога.|34|нет|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если доступно.|14|Да|  
|**TextData**|**ntext**|Текст сообщения об ошибке, относящейся к этому событию. Для событий, не формирующих сообщения об ошибке, данное поле остается незаполненным. Сообщение об ошибке может быть либо сообщением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо сообщением Windows.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|нет|  
  
  
