---
title: Работа с поставщиком WMI для событий сервера | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- event notifications [WMI]
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- Service Broker [WMI]
- WMI Provider for Server Events, connection strings
- WMI Provider for Server Events, Service Broker
- notifications [WMI]
- WMI Provider for Server Events, security
ms.assetid: cd974b3b-2309-4a20-b9be-7cfc93fc4389
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 98f1dfb796dbd30eb6e4d7f4e20d9bf37854d902
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-the-wmi-provider-for-server-events"></a>Работа с поставщиком WMI для событий сервера
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  В этом разделе приводятся рекомендации, которые следует учитывать при программировании с помощью поставщика WMI для событий сервера.  
  
## <a name="enabling-service-broker"></a>Включение компонента Service Broker  
 Поставщик WMI для событий сервера преобразует запросы на события WQL в уведомления о событиях в целевой базе данных. Понимание работы уведомлений о событиях полезно при программировании поставщика. Дополнительные [Поставщик WMI для событий сервера основные понятия о поставщике](http://technet.microsoft.com/library/ms180560.aspx)сведения см. в разделе.  
  
 В частности, поскольку уведомления о событиях, созданные поставщиком WMI, используют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отправки сообщений о событиях сервера, при формировании событий эта служба должна быть включена. Если программа запрашивает события на экземпляре сервера, необходимо включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в msdb этого экземпляра, поскольку здесь находится целевая служба [!INCLUDE[ssSB](../../includes/sssb-md.md)] (с именем SQL/Notifications/ProcessWMIEventProviderNotification/v1.0), создаваемая поставщиком. Если программа запрашивает события в базе данных или в определенном объекте базы данных, необходимо включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в этой базе данных-получателе. Если соответствующий компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не включен после развертывания приложения, то все события, формируемые базовым уведомлением о событиях, отправляются в очередь службы, которую использует уведомление о событиях, но они не возвращаются приложению инструментария WMI, пока не будет включен компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 Следующий запрос определяет, какой компонент Service Broker включен на экземпляре сервера, а также возвращает идентификатор GUID экземпляра компонента:  
  
```  
SELECT name, is_broker_enabled, service_broker_guid FROM sys.databases;  
```  
  
 Особый интерес представляет идентификатор GUID компонента Service Broker базы данных msdb, поскольку здесь находится целевая служба поставщика.  
  
 Чтобы включить [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных, используйте параметр ENABLE_BROKER SET [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) инструкции.  
  
## <a name="specifying-a-connection-string"></a>Задание строки соединения  
 Приложения указывают поставщику WMI для событий сервера экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соединяясь с пространством имен WMI, определяемым поставщиком. Служба Windows WMI сопоставляет это пространство имен с файлом поставщика Sqlwep.dll и загружает его в память. Каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет собственное пространство имен WMI, значение по умолчанию: \\ \\.\\ *корневой*\Microsoft\SqlServer\ServerEvents\\*имя_экземпляра*. *имя_экземпляра* по умолчанию равно MSSQLSERVER в установке по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions-and-server-authentication"></a>Разрешения и проверка подлинности сервера  
 Чтобы получить доступ к поставщику WMI для событий сервера, клиент, на котором выполняется приложение инструментария WMI, должен соответствовать прошедшему проверку имени входа или группе Windows в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который задан в строке соединения приложения.  
  
## <a name="permissions-and-event-notification-scope"></a>Разрешения и область уведомления о событиях  
 Поставщик WMI для событий сервера преобразует запросы WQL в уведомления о событиях в базе данных-получателе. Вследствие этого, вызывающее приложение должно иметь не только необходимые минимальные разрешения для доступа к поставщику, но и соответствующие разрешения в базе данных для создания требуемых уведомлений о событиях. Эти разрешения указаны ниже.  
  
-   Чтобы создать уведомление о событии в области базы данных, как минимум необходимо разрешение CREATE DATABASE DDL EVENT NOTIFICATION в текущей базе данных.  
  
-   Чтобы создать уведомление о событии для инструкции DDL в области сервера, как минимум необходимо разрешение CREATE DDL EVENT NOTIFICATION на сервере.  
  
-   Чтобы создать уведомление о событии для события трассировки, как минимум необходимо разрешение CREATE TRACE EVENT NOTIFICATION на сервере.  
  
-   Чтобы создать уведомление о событии в области очереди, для запроса как минимум необходимо разрешение ALTER для очереди.  
  
 Сведения об области запросов WQL см. в [Использование WQL с поставщиком WMI для событий сервера](http://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)разделе.  
  
 Продемонстрировать эффект области запросов можно с помощью приложения поставщика WMI, включающего следующий WQL-запрос:  
  
```  
SELECT * FROM ALTER_TABLE  
WHERE DatabaseName = "AdventureWorks2012"   
    AND SchemaName = "Person"  
    AND ObjectName = "Person"  
    AND ObjectType = "TABLE";  
```  
  
 Поставщик WMI преобразует этот запрос в уведомление о событии, создающееся в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Это означает, что вызывающий объект должен иметь разрешения на создание такого уведомления о событии, а именно, разрешение CREATE DATABASE DDL EVENT NOTIFICATION в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 Если WQL-запрос задает уведомление о событиях с областью действия на уровне сервера, например с помощью запроса SELECT * FROM ALTER_TABLE, то вызывающее приложение должно иметь разрешение на уровне сервера CREATE DDL EVENT NOTIFICATION. Обратите внимание, что уведомления о событиях уровня сервера хранятся в базе данных master. Можно использовать [sys.server_event_notifications](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md) представления для просмотра их метаданных каталога.  
  
> [!NOTE]  
>  Область уведомления о событии, созданном поставщиком WMI (сервер, база данных или объект) в конечном счете зависит от результата процесса проверки разрешений для поставщика WMI. На него влияет набор разрешений пользователя, вызывающего поставщик, и проверка базы данных, к которой выполняется запрос.  
>   
>  В предыдущем примере поставщик вначале пытается создать уведомление о событии с областью базы данных (`ON DATABASE`). Если поставщик убеждается, что база данных существует, и что вызывающий объект имеет необходимые разрешения для создания в ней уведомления о событии, регистрация проходит успешно. В противном случае поставщик пытается создать уведомление о событии на сервере (`ON SERVER`). Если предположить, что эта попытка окажется успешной, то все события `ALTER_TABLE`, возникающие на сервере, отправляются из процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в процесс службы WMI. Однако поставщик отфильтровывает все события, не применимые к базе данных `AdventureWorks` . Хотя этот процесс потенциально может увеличить сетевой трафик, необходимый для области события, он также обеспечивает гибкость, позволяя регистрировать запросы WQL в базе данных до их создания, а затем получая данные событий после создания базы данных и начала операций DDL в ней.  
  
## <a name="permissions-and-message-verification"></a>Разрешения и проверка сообщений  
 Поставщик WMI не отправляет сообщения для уведомлений о событиях, если выполняются оба следующих условия.  
  
-   Пользователь, создавший уведомление о событии с помощью поставщика WMI, больше не существует в базе данных или не имеет необходимых разрешений на создание такого уведомления о событии.  
  
-   Уведомления о событиях создаются для следующих событий:  
  
    -   DROP_LOGIN  
  
    -   ALTER_LOGIN  
  
    -   DROP_USER  
  
    -   ALTER_USER  
  
    -   ADD_ROLE_MEMBER  
  
    -   DROP_ROLE_MEMBER  
  
    -   ADD_SERVER_ROLE_MEMBER  
  
    -   DROP_SERVER_ROLE_MEMBER  
  
    -   DENY or REVOKE (применимо только к разрешениям ALTER DATABASE, ALTER ANY DATABASE EVENT NOTIFICATION, CREATE DATABASE DDL EVENT NOTIFICATION, CONTROL SERVER, ALTER ANY EVENT NOTIFICATION, CREATE DDL EVENT NOTIFICATION или CREATE TRACE EVENT NOTIFICATION.)  
  
## <a name="working-with-event-data-on-the-client-side"></a>Работа с данными событий на стороне клиента  
 После поставщик WMI для событий сервера создает уведомление о событии, необходимых в целевой базе данных, уведомление о событии отправляет данные события целевой службе в базе данных msdb, которая называется **SQL, уведомления и ProcessWMIEventProviderNotification /V1.0**. Целевая служба ставит событие в очередь **WMIEventProviderNotificationQueue** в базе данных **msdb**. (И очередь и служба динамически создаются поставщиком при первом соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) Затем поставщик считывает XML-данные события из этой очереди и преобразует их в данные MOF, прежде чем возвратить их в клиентское приложение. Данные MOF состоят из свойств события, запрашиваемого WQL-запросом в виде определения класса общей информационной модели (CIM). Каждое свойство имеет соответствующий тип CIM. Например, свойство `SPID` возвращается как тип CIM **Sint32**сведения см. в разделе. Типы CIM для каждого свойства отображаются в каждом классе событий в [поставщик WMI для событий классов и свойств сервера](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о поставщике WMI для событий сервера](http://technet.microsoft.com/library/ms180560.aspx)  
  
  
