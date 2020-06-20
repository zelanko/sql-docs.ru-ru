---
title: Класс событий Broker:Conversation | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Conversation event class
ms.assetid: 784707b5-cc67-46a3-8ae6-8f8ecf4b27c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f488f28f210826613b9fa3e8029121ab1f858e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85030636"
---
# <a name="brokerconversation-event-class"></a>Broker:Conversation, класс событий
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие **Broker:Conversation** , чтобы сообщать о ходе диалога компонента Service Broker.  
  
## <a name="brokerconversation-event-class-data-columns"></a>Столбцы данных класса событий Broker:Conversation  
  
|Столбец данных|Тип|Description|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|`int`|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|`int`|Идентификатор базы данных, указанный в инструкции USE *database* . Идентификатор базы данных по умолчанию, указанный в том случае, если инструкция USE *базы данных*не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных с помощью функции **DB_ID** .|3|Да|  
|**EventClass**|`int`|Тип захваченного класса событий. Всегда **124** для класса событий **Broker:Conversation**.|27|нет|  
|**EventSequence**|`int`|Порядковый номер этого события.|51|нет|  
|**EventSubClass**|`nvarchar`|Тип подкласса события. Предоставляет дополнительные сведения о каждом классе событий.|21|Да|  
|**GUID**|`uniqueidentifier`|Идентификатор диалога. Этот идентификатор передается в составе сообщения и является общим для обоих участников диалога.|54|нет|  
|**HostName**|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию **HOST_NAME** .|8|Да|  
|**IsSystem**|`int`|Указывает, произошло событие в системном или в пользовательском процессе.<br /><br /> 0 = пользовательский процесс<br /><br /> 1 = системный процесс|60|нет|  
|**LoginSid**|`image`|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**MethodName**|`nvarchar`|Группа сообщений, которой принадлежит диалог.|47|нет|  
|**NTDomainName**|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|`nvarchar`|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ObjectName**|`nvarchar`|Дескриптор диалога.|34|нет|  
|**Priority**|`int`|Уровень приоритета диалога|5|Да|  
|**RoleName**|`nvarchar`|Роль дескриптора диалога. Это либо **initiator** , либо **target**.|38|нет|  
|**ServerName**|`nvarchar`|Имя отслеживаемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|26|нет|  
|**Серьезность**|`int`|Уровень серьезности ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если данное событие сообщает об ошибке.|29|нет|  
|**SPID**|`int`|Идентификатор серверного процесса, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|`datetime`|Время начала события, если оно доступно.|14|Да|  
|**TextData**|`ntext`|Текущее состояние диалога. Это может быть:<br /><br /> **Так далее**. Запущен на отправку. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработал инструкцию BEGIN CONVERSATION для этого диалога, но не было отправлено ни одного сообщения.<br /><br /> **Si**. Запущен на прием. Другой экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] начал новый диалог с текущим экземпляром, но текущий экземпляр еще не завершил прием первого сообщения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может создать диалог в этом состоянии в том случае, если первая передача фрагментирована или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает сообщения с нарушением порядка следования. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может создать диалог сразу в состоянии CO, если первая передача, полученная для диалога, содержит первое сообщение целиком.<br /><br /> **Co**. Ведение диалога. Диалог установлен, и обе стороны диалога могут посылать сообщения. Для обычной службы основная часть обмена данными происходит, когда диалог находится в этом состоянии.<br /><br /> **Di**. Отключен на прием. Удаленной стороной диалога была выполнена инструкция END CONVERSATION. Состояние диалога остается неизменным до тех пор, пока локальная сторона диалога не выдаст сообщение END CONVERSATION. Приложение может продолжать получать сообщения для диалога. Поскольку удаленная сторона диалога закончила диалог, приложение не может отправлять сообщения в этом диалоге. Когда приложение выполняет инструкцию END CONVERSATION, диалог переходит в закрытое (CD) состояние.<br /><br /> **Сделать**. Отключен на отправку. Локальной стороной диалога была выполнена инструкция END CONVERSATION. Состояние диалога остается неизменным до тех пор, пока удаленная часть диалога не подтвердит сообщение END CONVERSATION. Приложение не может отправлять и получать сообщения для диалога. Когда удаленная сторона диалога подтверждает END CONVERSATION, диалог переходит в закрытое (CD) состояние.<br /><br /> **ER**. Ошибка. В данной конечной точке произошла ошибка. Столбцы Error, Severity и State содержат подробные данные о возникшей ошибке.<br /><br /> **Компакт-диск**. Закрыт. Конечная точка диалога больше не используется.|1|Да|  
|**Transaction ID**|`bigint`|Назначенный системой идентификатор транзакции.|4|нет|  
  
 В представленной ниже таблице перечислены значения подклассов для данного класса событий.  
  
|ID|Подкласс|Описание|  
|--------|--------------|-----------------|  
|1|SEND Message|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **отправки сообщения** , когда [!INCLUDE[ssDE](../../includes/ssde-md.md)] ВЫПОЛНЯЕТ инструкцию SEND.|  
|2|END CONVERSATION|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]формирует событие **END CONVERSATION** [!INCLUDE[ssDE](../../includes/ssde-md.md)] , когда ВЫПОЛНЯЕТ инструкцию END CONVERSATION, которая не включает предложение WITH ERROR.|  
|3|END CONVERSATION WITH ERROR|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]формирует **завершающее событие с ошибкой** , когда [!INCLUDE[ssDE](../../includes/ssde-md.md)] ВЫПОЛНЯЕТ инструкцию END CONVERSATION, ВКЛЮЧАЮЩУЮ предложение WITH ERROR.|  
|4|Broker Initiated Error|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **ошибки, инициированное брокером** , каждый раз, когда [!INCLUDE[ssSB](../../includes/sssb-md.md)] создает сообщение об ошибке. Например, если компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не может успешно направить сообщение для диалога, то создает сообщение об ошибке для диалога и формирует это событие. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не создает это событие, если прикладная программа завершает диалог с ошибкой.|  
|5|Terminate Dialog|[!INCLUDE[ssSB](../../includes/sssb-md.md)] прекратил диалог. [!INCLUDE[ssSB](../../includes/sssb-md.md)] прекращает диалоги в ответ на появление условий, не позволяющих продолжить диалог, но не являющихся ошибками или нормальным завершением диалога. Например, в случае удаления службы компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] прерывает все диалоги для этой службы.|  
|6|Received Sequenced Message|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает класс событий **Received последовательного сообщения** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , когда получает сообщение, содержащее порядковый номер сообщения. Все определяемые пользователем типы сообщений являются последовательными. [!INCLUDE[ssSB](../../includes/sssb-md.md)] формирует сообщение с нарушением порядка следования в двух случаях.<br /><br /> Сообщения об ошибках, формируемых компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)] , являются непоследовательными.<br /><br /> Подтверждения сообщений могут быть непоследовательными. Чтобы повысить эффективность, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] включает подтверждения сообщений в состав последовательного сообщения. Однако, если приложение не посылает последовательные сообщения в удаленную конечную точку в течение определенного периода времени, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] создает непоследовательное сообщение для подтверждения сообщения.|  
|7|Received END CONVERSATION|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает событие «Received END CONVERSATION», когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает сообщение «End Dialog» от другой стороны диалога.|  
|8|Received END CONVERSATION WITH ERROR|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **Received END CONVERSATION WITH ERROR** , когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает определяемую пользователем ошибку с другой стороны диалога. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не создает это событие, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает сообщение об определяемой посредником ошибке.|  
|9|Received Broker Error Message|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **Received Error Message (полученное сообщение об ошибке компонента Service Broker** ), когда [!INCLUDE[ssSB](../../includes/sssb-md.md)] получает определенное брокером сообщение об ошибке от другой стороны диалога. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не создает этого события, если компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] получает сообщение об ошибке, формируемое приложением.<br /><br /> Например, если текущая база данных содержит маршрут по умолчанию к базе данных пересылки, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] направляет сообщение с неизвестным именем службы в базу данных пересылки. Если база данных пересылки не может определить маршрут для сообщения, посредник в этой базе данных создает сообщение об ошибке и возвращает его в текущую базу данных. Если текущая база данных получает формируемое посредником сообщение об ошибке из базы данных пересылки, текущая база данных формирует событие **Received Broker Error Message** .|  
|10|Received END CONVERSATION Ack|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает класс событий **Received END CONVERSATION ACK** , когда другая сторона диалога подтверждает завершение диалогового окна или сообщения об ошибке, отправленного этой стороной диалога.|  
|11|BEGIN DIALOG|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **BEGIN DIALOG** , когда ядро СУБД ВЫПОЛНЯЕТ команду BEGIN DIALOG.|  
|12|Dialog Created|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает событие **создания диалогового окна** при [!INCLUDE[ssSB](../../includes/sssb-md.md)] создании конечной точки для диалогового окна. [!INCLUDE[ssSB](../../includes/sssb-md.md)] создает конечную точку каждый раз при установлении нового диалога, независимо от того, является текущая база данных инициатором или целью диалога.|  
|13|END CONVERSATION WITH CLEANUP|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует событие END CONVERSATION WITH CLEANUP, когда [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполняет инструкцию END CONVERSATION, в которую входит предложение WITH CLEANUP.|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
