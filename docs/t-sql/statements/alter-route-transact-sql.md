---
title: "ALTER ROUTE (Transact-SQL) | Документы Microsoft"
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
- ALTER_ROUTE_TSQL
- ALTER ROUTE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER ROUTE statement
- dropping routes
- modifying routes
- removing routes
- routes [Service Broker], modifying
ms.assetid: 8dfb7b16-3dac-4e1e-8c97-adf2aad07830
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 39e39b8688e2350d27e664b4a1517584c11df941
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-route-transact-sql"></a>ALTER ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет данные о существующем маршруте в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER ROUTE route_name  
WITH    
  [ SERVICE_NAME = 'service_name' [ , ] ]  
  [ BROKER_INSTANCE = 'broker_instance' [ , ] ]  
  [ LIFETIME = route_lifetime [ , ] ]  
  [ ADDRESS =  'next_hop_address' [ , ] ]  
  [ MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *route_name*  
 Имя изменяемого маршрута. Не могут быть указаны имена сервера, базы данных и схемы.  
  
 на  
 Представляет предложения, определяющие изменяемый маршрут.  
  
 Параметры SERVICE_NAME **= "***service_name***"**  
 Указывает имя удаленной службы, находящейся по этому маршруту. *Service_name* должно точно совпадать, используется имя удаленной службы. [!INCLUDE[ssSB](../../includes/sssb-md.md)]использует сравнение байт за байтом *service_name*. Другими словами, при сравнении учитывается регистр и не применяются текущие параметры сортировки. Маршрут с именем службы **«SQL/ServiceBroker/BrokerConfiguration»** маршрут для службы уведомления конфигурации брокера. В маршруте к этой службе может не указываться экземпляр компонента Service Broker.  
  
 Если опущено предложение SERVICE_NAME, имя службы для маршрута не меняется.  
  
 BROKER_INSTANCE **= "***broker_instance***"**  
 Указывает базу данных, в которой расположена целевая служба. *Broker_instance* параметр должен быть идентификатор экземпляра брокера для удаленной базы данных, который можно получить, выполнив следующий запрос в выбранной базе данных:  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 Если опущено предложение BROKER_INSTANCE, экземпляр брокера для маршрута не меняется.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 Время СУЩЕСТВОВАНИЯ  **=**  *route_lifetime*  
 Время в секундах, в течение которого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит маршрут в таблице маршрутизации. По истечении этого времени действие маршрута истекает, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при выборе маршрута для новых диалогов далее его не рассматривает. Если данное предложение опущено, срок жизни маршрута не меняется.  
  
 АДРЕС **= "***next_hop_address*  
 Указывает сетевой адрес для данного маршрута. *Next_hop_address* задает адрес TCP/IP в следующем формате:  
  
 **TCP: / /** { *dns_name* | *netbios_name* |*ip_address* } **:**  *номер_порта*  
  
 Указанный *Номер_порта* должен соответствовать номеру порта для [!INCLUDE[ssSB](../../includes/sssb-md.md)] конечной точки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на указанном компьютере. Его можно получить, выполнив к выбранной базе данных следующий запрос:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Если указывается значение **'LOCAL'** для *next_hop_address*, сообщение доставляется службе текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если указывается значение **'TRANSPORT'** для *next_hop_address*, сетевой адрес определяется на основе адреса сетевого имени службы. Маршрут, указывающий **'TRANSPORT'** можно указать имя или компонента broker экземпляра службы.  
  
 Когда *next_hop_address* является основным сервером для зеркала базы данных, необходимо также указать MIRROR_ADDRESS для зеркального сервера. Иначе данный маршрут не перейдет к зеркальному серверу при отработке отказа автоматически.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 Параметр MIRROR_ADDRESS **= "***next_hop_mirror_address***"**  
 Указывает сетевой адрес для зеркального сервера зеркальной пары, чей основной сервер находится в *next_hop_address*. *Next_hop_mirror_address* задает адрес TCP/IP в следующем формате:  
  
 **TCP: / /**{ *dns_name* | *netbios_name* | *ip_address* } **:**  *номер_порта*  
  
 Указанный *Номер_порта* должен соответствовать номеру порта для [!INCLUDE[ssSB](../../includes/sssb-md.md)] конечной точки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на указанном компьютере. Его можно получить, выполнив к выбранной базе данных следующий запрос:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Если указано предложение MIRROR_ADDRESS, маршрут должен указать предложения SERVICE_NAME и BROKER_INSTANCE. Маршрут, указывающий **'LOCAL'** или **'TRANSPORT'** для *next_hop_address* , нельзя указывать зеркальный адрес.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
## <a name="remarks"></a>Замечания  
 Таблица маршрутизации, хранящая маршруты представляет таблицу метаданных, могут быть получены с помощью **sys.routes** представления каталога. Таблица маршрутизации может быть обновлена только с помощью инструкций CREATE ROUTE, ALTER ROUTE и DROP ROUTE.  
  
 Предложения, не указанные в команде ALTER ROUTE, остаются неизменными. Таким образом, инструкция ALTER не может быть использована для указания того, что маршрут не блокируется по времени, что он соответствует какому-либо имени службы или экземпляру брокера. Чтобы изменить эти параметры маршрута, необходимо удалить существующий маршрут и создать новый с обновленными сведениями.  
  
 Если указывается значение **'TRANSPORT'** для *next_hop_address*, сетевой адрес определяется на основе имени службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]может успешно обрабатывать имена служб, начинающиеся с сетевого адреса в формате, который является допустимым для *next_hop_address*. Службы с именами, содержащими действительные сетевые адреса, создадут маршрут к сетевому адресу в имени службы.  
  
 Таблица маршрутизации может содержать любое количество маршрутов, в которых указаны имя службы, сетевой адрес или идентификатор экземпляра брокера. В этих случаях компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] производит выбор маршрута при помощи процедуры поиска наиболее точного соответствия сведений, указанных в диалоге, данным, содержащимся в таблице маршрутизации.  
  
 Чтобы изменить свойство AUTHORIZATION для службы, используйте инструкцию ALTER AUTHORIZATION.  
  
## <a name="permissions"></a>Permissions  
 Разрешение на изменение маршрута по умолчанию обладает владелец маршрута, члены **db_ddladmin** или **db_owner** фиксированной роли базы данных и члены **sysadmin** исправлена роль сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-service-for-a-route"></a>A. Изменение службы для маршрута  
 В следующем примере маршрут `ExpenseRoute` изменяется таким образом, чтобы указывать на удаленную службу `//Adventure-Works.com/Expenses`.  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     SERVICE_NAME = '//Adventure-Works.com/Expenses';  
```  
  
### <a name="b-changing-the-target-database-for-a-route"></a>Б. Изменение целевой базы данных для маршрута  
 В следующем примере целевая база данных для маршрута `ExpenseRoute` изменяется на базу данных, определяемую уникальным идентификатором `D8D4D268-00A3-4C62-8F91-634B89B1E317.`  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317';  
```  
  
### <a name="c-changing-the-address-for-a-route"></a>В. Изменение адреса маршрута  
 В следующем примере сетевой адрес для маршрута `ExpenseRoute` к порту TCP `1234` на узле изменяется на IP-адрес `10.2.19.72`.  
  
```  
ALTER ROUTE ExpenseRoute   
   WITH   
     ADDRESS = 'TCP://10.2.19.72:1234';  
```  
  
### <a name="d-changing-the-database-and-address-for-a-route"></a>Г. Изменение базы данных и адреса маршрута  
 В следующем примере сетевой адрес маршрута `ExpenseRoute` меняется на TCP-порт `1234` на узле с DNS-именем `www.Adventure-Works.com`. Кроме того, целевая база данных заменяется на базу данных, определяемую уникальным идентификатором `D8D4D268-00A3-4C62-8F91-634B89B1E317`.  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317',  
     ADDRESS = 'TCP://www.Adventure-Works.com:1234';  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ROUTE (Transact-SQL)](../../t-sql/statements/create-route-transact-sql.md)   
 [DROP ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

