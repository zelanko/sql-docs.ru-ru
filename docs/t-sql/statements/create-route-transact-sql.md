---
title: "Создание МАРШРУТА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_ROUTE_TSQL
- ROUTE
- CREATE ROUTE
- ROUTE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- lifetimes [Service Broker]
- routes [Service Broker], creating
- forwarding brokers [SQL Server]
- service names [Service Broker]
- database mirroring [SQL Server], routing
- expired routes [SQL Server]
- activating routes
- CREATE ROUTE statement
ms.assetid: 7e695364-1a98-4cfd-8ebd-137ac5a425b3
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 767be5069d65c11dad849a8fc32f5b15296a4eda
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-route-transact-sql"></a>CREATE ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новый маршрут к таблице маршрутов для текущей базы данных. Для исходящих сообщений компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] определяет маршруты, проверяя таблицу маршрутов в локальной базе данных. Для сообщений диалогов, начатых в другом экземпляре, включая пересылаемые, сообщения [!INCLUDE[ssSB](../../includes/sssb-md.md)] проверяет маршруты в **msdb**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE ROUTE route_name  
[ AUTHORIZATION owner_name ]  
WITH    
   [ SERVICE_NAME = 'service_name', ]  
   [ BROKER_INSTANCE = 'broker_instance_identifier' , ]  
   [ LIFETIME = route_lifetime , ]  
   ADDRESS =  'next_hop_address'  
   [ , MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *route_name*  
 Имя создаваемого маршрута. Новый маршрут создается в текущей базе данных и принадлежит участнику, указанному в предложении AUTHORIZATION. Не могут быть указаны имена сервера, базы данных и схемы. *Route_name* должен быть допустимым **sysname**.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Устанавливает заданного пользователя или роль базы данных в качестве владельца маршрута. *Owner_name* может быть именем любого допустимого пользователя или роли, если текущий пользователь является членом либо **db_owner** предопределенной роли базы данных или **sysadmin** предопределенной роли сервера. В противном случае *owner_name* должен быть именем текущего пользователя, имя пользователя, что у текущего пользователя есть разрешение IMPERSONATE для или имя роли, к которой принадлежит текущий пользователь. Если это предложение опущено, то маршрут принадлежит текущему пользователю.  
  
 на  
 Представляет предложения, которые определяют создаваемый маршрут.  
  
 SERVICE_NAME = **'***service_name***'**  
 Указывает имя удаленной службы, находящейся по этому маршруту. *Service_name* должно точно совпадать, используется имя удаленной службы. [!INCLUDE[ssSB](../../includes/sssb-md.md)]использует сравнение байт за байтом *service_name*. Другими словами, при сравнении учитывается регистр и не применяются текущие параметры сортировки. Если аргумент SERVICE_NAME опущен, этот маршрут соответствует любому имени службы, но имеет более низкий приоритет, чем маршрут с аргументом SERVICE_NAME. Маршрут с именем службы **«SQL/ServiceBroker/BrokerConfiguration»** маршрут для службы уведомления конфигурации брокера. В маршруте к этой службе может не указываться экземпляр компонента Service Broker.  
  
 BROKER_INSTANCE = **"***broker_instance_identifier***"**  
 Указывает базу данных, в которой расположена целевая служба. *Broker_instance_identifier* параметр должен быть идентификатор экземпляра брокера для удаленной базы данных, который можно получить, выполнив следующий запрос в выбранной базе данных:  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID()  
```  
  
 Если предложение BROKER_INSTANCE опущено, то маршрут соответствует любому экземпляру брокера. Маршрут, соответствующий любому экземпляру брокера, имеет более высокий приоритет соответствия, чем маршрут с явным экземпляром брокера, когда диалог не указывает экземпляр брокера. Для диалогов, указывающих экземпляр брокера, маршрут с экземпляром брокера имеет более высокий приоритет, чем маршрут, соответствующий любому экземпляру брокера.  
  
 LIFETIME **=***route_lifetime*  
 Время в секундах, в течение которого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит маршрут в таблице маршрутизации. По истечении этого времени действие маршрута истекает, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при выборе маршрута для новых диалогов далее его не рассматривает. Если это предложение опущено, *route_lifetime* имеет значение NULL и маршрута никогда не истекает.  
  
 АДРЕС **= "***next_hop_address***"**  
 Указывает сетевой адрес для данного маршрута. *Next_hop_address* задает адрес TCP/IP в следующем формате:  
  
 **TCP://**{ *dns_name* | *netbios_name* | *ip_address* } **:***port_number*  
  
 Указанный *Номер_порта* должен соответствовать номеру порта для [!INCLUDE[ssSB](../../includes/sssb-md.md)] конечной точки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на указанном компьютере. Его можно получить, выполнив к выбранной базе данных следующий запрос:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Если служба находится на зеркальной базе данных, необходимо также указать MIRROR_ADDRESS для другого экземпляра зеркальной базы данных. В противном случае он не будет учитываться в маршруте.  
  
 Если указывается значение **'LOCAL'** для *next_hop_address*, сообщение доставляется службе текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если указывается значение **'TRANSPORT'** для *next_hop_address*, сетевой адрес определяется на основе адреса сетевого имени службы. Маршрут, указывающий **'TRANSPORT'** может не указывать имя или компонента broker экземпляра службы.  
  
 MIRROR_ADDRESS **='***next_hop_mirror_address***'**  
 Указывает сетевой адрес для зеркальной базы данных с одним зеркальная база данных находится в *next_hop_address*. *Next_hop_mirror_address* задает адрес TCP/IP в следующем формате:  
  
 **TCP://**{ *dns_name* | *netbios_name* | *ip_address* } **:** *port_number*  
  
 Указанный *Номер_порта* должен соответствовать номеру порта для [!INCLUDE[ssSB](../../includes/sssb-md.md)] конечной точки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на указанном компьютере. Его можно получить, выполнив к выбранной базе данных следующий запрос:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Если указано предложение MIRROR_ADDRESS, маршрут должен указать предложения SERVICE_NAME и BROKER_INSTANCE. Маршрут, указывающий **'LOCAL'** или **'TRANSPORT'** для *next_hop_address* , нельзя указывать зеркальный адрес.  
  
## <a name="remarks"></a>Remarks  
 Таблица маршрутизации, хранящая маршруты представляет таблицу метаданных, которые могут быть получены с помощью **sys.routes** представления каталога. Это представление каталога может быть обновлено только с помощью инструкций CREATE ROUTE, ALTER ROUTE и DROP ROUTE.  
  
 По умолчанию таблица маршрутов в каждой базе данных содержит один маршрут. Этот маршрут называется **AutoCreatedLocal**. Маршрут указывает **'LOCAL'** для *next_hop_address* и соответствует любому идентификатору службы имя и broker экземпляра.  
  
 Если указывается значение **'TRANSPORT'** для *next_hop_address*, сетевой адрес определяется на основе имени службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]может успешно обрабатывать имена служб, начинающиеся с сетевого адреса в формате, который является допустимым для *next_hop_address*.  
  
 Таблица маршрутов может содержать любое количество маршрутов, указывающих одну и ту же службу, сетевой адрес и идентификатор экземпляра брокера. В этих случаях компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] производит выбор маршрута при помощи процедуры поиска наиболее точного соответствия сведений, указанных в диалоге, данным, содержащимся в таблице маршрутизации.  
  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не удаляет из таблицы маршрутизации маршруты с истекшим сроком действия. Маршрут с истекшим сроком можно активировать с помощью инструкции ALTER ROUTE.  
  
 Маршрут не может быть временным объектом. Имена маршрутов, начинающиеся с  **#**  разрешены, но являются постоянными объектами.  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на Создание маршрута по умолчанию принадлежит членам **db_ddladmin** или **db_owner** предопределенных ролей базы данных и **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-tcpip-route-by-using-a-dns-name"></a>A. Создание TCP/IP-маршрута с помощью DNS-имени  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/Expenses`. Маршрут указывает, что сообщения для этой службы передаются по протоколу TCP на порт `1234` узла, который определяется DNS-именем `www.Adventure-Works.com`. Целевой сервер доставляет сообщения по прибытию их на экземпляр брокера, определенный уникальным идентификатором `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://www.Adventure-Works.com:1234' ;  
```  
  
### <a name="b-creating-a-tcpip-route-by-using-a-netbios-name"></a>Б. Создание TCP/IP-маршрута с помощью NetBIOS-имени  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/Expenses`. Маршрут указывает, что сообщения для этой службы передаются по протоколу TCP на порт `1234` узла, который определяется NetBIOS-именем `SERVER02`. По прибытии сообщения целевой сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доставляет его экземпляру базы данных, определенному уникальным идентификатором `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH   
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://SERVER02:1234' ;  
```  
  
### <a name="c-creating-a-tcpip-route-by-using-an-ip-address"></a>В. Создание TCP/IP-маршрута с помощью IP-адреса  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/Expenses`. Маршрут указывает, что сообщения для этой службы передаются по протоколу TCP на порт `1234` узла с IP-адресом `192.168.10.2`. По прибытии сообщения целевой сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доставляет его экземпляру брокера, определенному уникальным идентификатором `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://192.168.10.2:1234' ;  
```  
  
### <a name="d-creating-a-route-to-a-forwarding-broker"></a>Г. Создание маршрута к брокеру пересылки  
 В следующем примере создается маршрут к перенаправляющему брокеру на сервере `dispatch.Adventure-Works.com`. Поскольку не заданы ни имя службы, ни идентификатор экземпляра брокера, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует этот маршрут для служб, маршруты которых не определены.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    ADDRESS = 'TCP://dispatch.Adventure-Works.com' ;   
```  
  
### <a name="e-creating-a-route-to-a-local-service"></a>Д. Создание маршрута к локальной службе  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/LogRequests` в том же экземпляре, что и маршрут.  
  
```  
CREATE ROUTE LogRequests  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/LogRequests',  
    ADDRESS = 'LOCAL' ;  
```  
  
### <a name="f-creating-a-route-with-a-specified-lifetime"></a>Е. Создание маршрута с заданным временем существования  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/Expenses`. Срок жизни маршрута равен `259200` секундам, что составляет 72 часа.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    LIFETIME = 259200,  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234' ;  
```  
  
### <a name="g-creating-a-route-to-a-mirrored-database"></a>Ж. Создание маршрута к зеркальной базе данных  
 В следующем примере создается маршрут к службе `//Adventure-Works.com/Expenses`. Эта служба размещена на зеркальной базе данных. Одна из зеркальных баз данных расположена по адресу `services.Adventure-Works.com:1234`, вторая — по адресу `services-mirror.Adventure-Works.com:1234`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = '69fcc80c-2239-4700-8437-1001ecddf933',  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234',   
    MIRROR_ADDRESS = 'TCP://services-mirror.Adventure-Works.com:1234' ;  
```  
  
### <a name="h-creating-a-route-that-uses-the-service-name-for-routing"></a>З. Создание маршрута, использующего для маршрутизации имя службы  
 В следующем примере создается маршрут, который использует имя службы для определения сетевого адреса, на который будут отправляться сообщения. Обратите внимание, что маршрут, указывающий `'TRANSPORT'` в качестве сетевого адреса, имеет более низкий приоритет совпадения, чем другие маршруты.  
  
```  
CREATE ROUTE TransportRoute  
    WITH ADDRESS = 'TRANSPORT' ;  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-route-transact-sql.md)   
 [DROP ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
