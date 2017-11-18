---
title: "Драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 27b51025180a1c9a2463c49401589ab459e7ecaf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Поддержка высокой доступности и аварийного восстановления в драйвере JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе обсуждаются [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддержку высокого уровня доступности и аварийного восстановления — [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Дополнительные сведения о среде [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]см. в электронной документации по [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] .  
  
 Начиная с версии 4.0 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], можно указать прослушиватель группы доступности (высокого уровня доступности, аварийного восстановления) группы доступности (AG) в свойстве соединения. Если [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] подключено приложение базы данных AlwaysOn, которая выполняет отработку отказа, первоначальное соединение разрывается и приложение должно установить новое соединение для продолжения работы после отработки отказа. Следующие [свойства соединения](../../connect/jdbc/setting-the-connection-properties.md) были добавлены в [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]:  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
Указать multiSubnetFailover = true, при подключении к прослушивателю группы доступности из группы доступности или экземпляра отказоустойчивого кластера. Обратите внимание, что **multiSubnetFailover** по умолчанию — false. Используйте **applicationIntent** объявить тип рабочей нагрузки приложения. В разделах ниже для получения дополнительных сведений.
 
Начиная с версии Microsoft JDBC Driver 6.0 для SQL Server, новое свойство соединения **transparentNetworkIPResolution** (TNIR) добавляется для прозрачное подключение для групп доступности AlwaysOn или сервер, который имеет связанные несколько IP-адресов. Когда **transparentNetworkIPResolution** имеет значение true, драйвер пытается подключиться к первый IP-адрес. Если первая попытка завершается неудачно, драйвер пытается подключиться всех IP-адресов в параллельном режиме до истечения времени ожидания, отменяя все ожидающие попытки подключения, когда один из них завершается успешно.   

Учтите, что:
* transparentNetworkIPResolution имеет значение true, если по умолчанию
* transparentNetworkIPResolution учитывается, если multiSubnetFailover имеет значение true
* transparentNetworkIPResolution учитывается, если используется зеркальное отображение базы данных
* transparentNetworkIPResolution учитывается, если существует более чем 64 IP-адресов
* Когда transparentNetworkIPResolution имеет значение true, первая попытка соединения используется значение времени ожидания 500 мс. REST попыток соединения, выполните ту же логику, как и функция multiSubnetFailover. 

> [!NOTE]  
Если вы используете Microsoft JDBC Driver 4.2 (или уменьшить) для SQL Server и **multiSubnetFailover** имеет значение false, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] пытается подключиться к первому IP-адресу. Если [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не удается установить соединение с первый IP-адрес, то соединение завершается ошибкой. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Не будет пытаться подключиться к любой последующей IP-адреса, связанного с сервером. 

  
> [!NOTE]  
>  Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover  
 Всегда указывайте **multiSubnetFailover = true** при подключении к прослушивателю группы доступности из [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] группы доступности или [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] экземпляра отказоустойчивого кластера. **multiSubnetFailover** обеспечивает ускоренную отработку отказа для всех групп доступности и экземпляров отказоустойчивых кластеров в [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] и значительно уменьшит время отработки отказа для топологий AlwaysOn с одной или несколькими подсетями. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. Во время отработки отказа в подсети [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет агрессивно повторять попытки соединения по протоколу TCP.  
  
 **MultiSubnetFailover** свойство соединения указывает, что приложение развертывается в группе доступности или экземпляра отказоустойчивого кластера и что [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] попытается соединиться с базой данных на сервере-источнике [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра, пытаясь подключиться ко всем IP-адресов. Когда **MultiSubnetFailover = true** указан для соединения, клиент повторяет попытку соединения по TCP быстрее, чем интервалов повторной передачи TCP операционной системы по умолчанию. Это позволяет ускорить восстановление соединения после отработки отказа в группе доступности AlwaysOn или в экземпляре отказоустойчивого кластера AlwaysOn; метод может применяться к группам доступности и экземплярам отказоустойчивых кластеров как с одной, так и с несколькими подсетями.  
  
 Дополнительные сведения о ключевых словах строки подключения в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Указание **multiSubnetFailover = true** при соединении с объектом, кроме прослушивателя группы доступности или экземпляра отказоустойчивого кластера может привести к отрицательно влияет на производительность и не поддерживается.  
  
 Если диспетчер безопасности не установлен, то виртуальная машина Java кэширует виртуальные IP-адреса (VIP) на ограниченный период времени (по умолчанию определяемый реализацией JDK и свойствами Java networkaddress.cache.ttl и networkaddress.cache.negative.ttl). Если диспетчер безопасности JDK установлен, то виртуальная машина Java будет кэшировать адреса VIP, причем кэш по умолчанию не обновляется. Необходимо установить «время существования» для кэша виртуальной машины Java (networkaddress.cache.ttl) в один день. Если этого не сделать, то старые значения не будут исключаться из кэша виртуальной машины Java при добавлении или обновлении адресов VIP. Дополнительные сведения о параметрах networkaddress.cache.ttl и networkaddress.cache.negative.ttl см. в разделе [http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Следуйте приведенным ниже рекомендациям для подключения к серверу в группе доступности или экземпляру отказоустойчивого кластера.  
  
-   Драйвер выдаст ошибку, если **instanceName** в той же строке подключения, что используется свойство подключения **multiSubnetFailover** свойство соединения. Это связано с тем, что браузер SQL Server в группе доступности не используется. Однако если **Номер_порта** также указано свойство соединения, то драйвер будет использовать **instanceName** и использовать **Номер_порта**.  
  
-   Используйте **multiSubnetFailover** свойство соединения при подключении к одной или несколькими подсетями, это улучшит производительность для обоих.  
  
-   Чтобы установить соединение с группой доступности, указывайте ее прослушиватель в строке подключения вместо сервера. Например, jdbc:sqlserver://VNN1.  
  
-   При установлении соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], настроенным на работу с более чем 64 IP-адресами, будет возникать ошибка соединения.  
  
-   Поведение приложения, использующего **multiSubnetFailover** свойство соединения не зависит от типа проверки подлинности: [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, проверка подлинности Kerberos или проверку подлинности Windows.  
  
-   Увеличьте значение **loginTimeout** чтобы обеспечить отработку отказов и сократить число повторных попыток подключения приложения.  
  
-   Распределенные транзакции не поддерживаются.  
  
 Если маршрутизация только для чтения неактивна, то подключение к местоположению вторичной реплики в группе доступности завершится ошибкой в следующих случаях:  
  
1.  Если местоположение вторичных реплик не настроено для приема подключений.  
  
2.  Если приложение использует **applicationIntent = ReadWrite** (описано ниже) и местоположение дополнительных реплик настроено для доступа только для чтения.  
  
 При соединении произойдет ошибка, если первичная реплика настроена для отклонения рабочих нагрузок только для чтения, а строка подключения содержит **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Переход с зеркального отображения базы данных на использование кластеров с несколькими подсетями  
 При обновлении [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] приложения, которое в настоящее время использует зеркальное отображение базы данных в сценарии с несколькими подсетями, необходимо удалить **failoverPartner** свойства соединения и замените ее на **multiSubnetFailover**  значение **true** и заменить имя сервера в строке соединения с прослушивателем группы доступности. Если в строке подключения используются **failoverPartner** и **multiSubnetFailover = true**, то драйвер выдаст ошибку. Тем не менее если в строке подключения используются **failoverPartner** и **multiSubnetFailover = false** (или **ApplicationIntent = ReadWrite**), приложение будет использовать базу данных зеркальное отображение.  
  
 Драйвер возвращает ошибку, если базы данных-источника в группе Доступности используется зеркальное отображение базы данных и **multiSubnetFailover = true** используется в строке подключения, которая подключается к основной базе данных вместо к группе доступности прослушиватель.  
  
## <a name="specifying-application-intent"></a>Задание намерения приложения  
 Когда **applicationIntent = ReadOnly**, клиент запрашивает рабочую нагрузку только для чтения при подключении к базе данных с поддержкой AlwaysOn. Сервер принудительно применяет намерение при установке соединения и при выполнении инструкции USE, но только для баз данных, поддерживающих AlwaysOn.  
  
 **ApplicationIntent** ключевое слово не работает с базами данных прежних версий, только для чтения.  
  
 База данных может допускать или не допускать рабочую нагрузку чтения для целевой базы данных AlwaysOn. (Это выполняется с использованием предложения **ALLOW_CONNECTIONS** инструкций **PRIMARY_ROLE** и **SECONDARY_ROLE**[!INCLUDE[tsql](../../includes/tsql_md.md)].)  
  
 **ApplicationIntent** ключевое слово используется для включения маршрутизации только для чтения.  
  
## <a name="read-only-routing"></a>Маршрутизация только для чтения  
 Маршрутизация только для чтения — это функция, которая способна обеспечить доступность реплики базы данных только для чтения. Включение маршрутизации только для чтения  
  
1.  Необходимо установить соединение с прослушивателем группы доступности AlwaysOn.  
  
2.  **ApplicationIntent** ключевое слово строки подключения должно быть присвоено **ReadOnly**.  
  
3.  Группа доступности должна быть настроена администратором базы данных на поддержку маршрутизации только для чтения.  
  
 Возможно, что не все из нескольких соединений, использующих маршрутизацию только для чтения, будут подключаться к одной и той же реплике только для чтения. Изменения в синхронизации баз данных или в конфигурации маршрутизации сервера могут привести к тому, что клиент будет подключаться к различным репликам только для чтения. Чтобы убедиться, что все запросы только для чтения подключаться к той же репликой только для чтения, не указывайте прослушиватель группы доступности или виртуальный IP-адрес для **serverName** ключевое слово строки подключения. Вместо этого укажите имя экземпляра, доступного только для чтения.  
  
 Маршрутизация только для чтения может занять больше времени, чем подключение к источнику, так как при этом сначала производится соединение с источником, а затем поиск наилучшего, доступного для чтения получателя. Учитывая этот факт, следует увеличить время ожидания входа в систему.  
  
## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Новые методы, поддерживающие multiSubnetFailover и applicationIntent  
 Следующие методы обеспечивают программный доступ к **multiSubnetFailover**, **applicationIntent** и **transparentNetworkIPResolution** строки подключения ключевые слова:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 **GetMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** и **setTransparentNetworkIPResolution** методы, также добавляются в [класса SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [ Класс SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), и [класса SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
## <a name="ssl-certificate-validation"></a>Проверка сертификатов SSL  
 Группа доступности состоит из нескольких физических серверов. [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]добавлена поддержка **альтернативное имя субъекта** в сертификатах SSL, что несколько узлов могут быть связаны с тем же сертификатом. Дополнительные сведения о протоколе SSL см. в разделе [основные сведения о поддержке SSL](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md)  
  
  

