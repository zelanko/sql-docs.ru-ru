---
title: Поддержка высокой доступности и аварийного восстановления в JDBC Driver | Документы Майкрософт
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6e760523026251463f80d7f7e3e14b7e52b36ab2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781534"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Поддержка высокой доступности и аварийного восстановления в драйвере JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе рассматривается поддержка [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] высокой доступности с аварийным восстановлением ― [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Дополнительные сведения о среде [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]см. в электронной документации по [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 Начиная с версии 4.0 драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] в свойствах подключения можно указать прослушиватель группы доступности (высокой доступности и аварийного восстановления). Если приложение [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] подключается к базе данных AlwaysOn, которая выполняет отработку отказа, то первоначальное подключение разрывается и приложение должно открыть новое подключение, чтобы продолжить работу после обработки отказа. В версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] добавлены следующие [свойства подключения](../../connect/jdbc/setting-the-connection-properties.md):  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
Укажите multiSubnetFailover=true при подключении к прослушивателю группы доступности или экземпляру отказоустойчивого кластера. Обратите внимание, что **multiSubnetFailover** по умолчанию — false. Используйте **applicationIntent** для объявления типа рабочей нагрузки приложения. См. Дополнительные сведения о разделах ниже.
 
Начиная с версии Microsoft JDBC Driver 6.0 для SQL Server, новое свойство соединения **transparentNetworkIPResolution** для групп доступности Always On или на сервере, который имеет для прозрачное подключение добавляется (TNIR.) связанные несколько IP-адреса. Когда **transparentNetworkIPResolution** имеет значение true, драйвер пытается подключиться к первый IP-адрес. Если первая попытка завершается неудачей, драйвер пытается подключиться для всех IP-адресов в параллельном режиме, пока не истечет время ожидания, отменяя все ожидающие попытки подключения, когда один из них завершается успешно.   

Следует учитывать, что:
* transparentNetworkIPResolution имеет значение true, по умолчанию
* transparentNetworkIPResolution учитывается, если multiSubnetFailover имеет значение true
* transparentNetworkIPResolution учитывается, если используется зеркальное отображение базы данных
* transparentNetworkIPResolution учитывается, если существует более чем 64 IP-адресов
* Если transparentNetworkIPResolution имеет значение true, первая попытка соединения использует значение времени ожидания 500 миллисекунд. REST попыток соединения выполните ту же логику, как и в функцию multiSubnetFailover. 

> [!NOTE]
> Если вы используете Microsoft JDBC Driver 4.2 (или уменьшить) для SQL Server и **multiSubnetFailover** имеет значение false, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] пытается подключиться к первый IP-адрес. Если [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не может установить подключение к первому IP-адресу, то подключение завершается сбоем. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не будет повторять попытку подключения к другим IP-адресам, связанным с сервером. 
> 
> 
> [!NOTE]
>  Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover  
 Всегда указывайте **MultiSubnetFailover=True** при соединении с прослушивателем группы доступности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **multiSubnetFailover** позволяет группам доступности и экземплярам отказоустойчивого кластера в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] быстрее выполнить отработку отказа, а также значительно сократить время перехода на другой ресурс для топологий AlwaysOn с одной подсетью или несколькими. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. При отработке отказа подсети [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет активно повторять попытки установить TCP-подключение.  
  
 Свойство подключения **multiSubnetFailover** указывает, что приложение развертывается в группе доступности или экземпляре отказоустойчивого кластера, а также что [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] попытается подключиться ко всем IP-адресам базы данных в первичном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда для подключения установлено свойство **MultiSubnetFailover=true**, клиент будет пытаться повторно установить TCP-подключение с более частым интервалом, чем заданные в операционной системе интервалы повторной отправки TCP-пакетов по умолчанию. Это позволяет ускорить восстановление соединения после отработки отказа в группе доступности AlwaysOn или в экземпляре отказоустойчивого кластера AlwaysOn; метод может применяться к группам доступности и экземплярам отказоустойчивых кластеров как с одной, так и с несколькими подсетями.  
  
 Дополнительные сведения о ключевых словах строки подключения в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Указание **multiSubnetFailover=true** при подключении к объекту, отличному от прослушивателя группы доступности или экземпляра отказоустойчивого кластера, может привести к снижению производительности и не поддерживается.  
  
 Если диспетчер безопасности не установлен, то виртуальная машина Java кэширует виртуальные IP-адреса (VIP) на ограниченный период времени (по умолчанию определяемый реализацией JDK и свойствами Java networkaddress.cache.ttl и networkaddress.cache.negative.ttl). Если диспетчер безопасности JDK установлен, то виртуальная машина Java будет кэшировать адреса VIP, причем кэш по умолчанию не обновляется. Необходимо установить «время существования» для кэша виртуальной машины Java (networkaddress.cache.ttl) в один день. Если этого не сделать, старые значения не будут исключаться из кэша виртуальной машины Java при добавлении или обновлении адресов VIP. Дополнительные сведения о параметрах networkaddress.cache.ttl и networkaddress.cache.negative.ttl см. в разделе [ https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html ](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Следуйте приведенным ниже рекомендациям для подключения к серверу в группе доступности или экземпляру отказоустойчивого кластера.  
  
-   Драйвер выдаст ошибку, если **instanceName** в ту же строку подключения, как используется свойство подключения **multiSubnetFailover** свойство соединения. Это связано с тем, что браузер SQL Server в группе доступности не используется. Тем не менее если **Номер_порта** также указано свойство соединения, то драйвер не будет **instanceName** и использовать **Номер_порта**.  
  
-   Используйте свойство подключения **multiSubnetFailover** при подключении к одной подсети или нескольким — это благоприятно скажется на производительности в любом случае.  
  
-   Чтобы установить соединение с группой доступности, указывайте ее прослушиватель в строке подключения вместо сервера. Например, jdbc:sqlserver://VNN1.  
  
-   При установлении соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], настроенным на работу с более чем 64 IP-адресами, будет возникать ошибка соединения.  
  
-   Режим работы приложения, использующего свойство подключения **multiSubnetFailover**, не зависит от типа проверки подлинности — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Kerberos или Windows.  
  
-   Значение **loginTimeout** можно увеличить с учетом времени отработки отказа и для уменьшения количества попыток приложения повторно установить подключение.  
  
-   Распределенные транзакции не поддерживаются.  
  
 Если маршрутизация только для чтения неактивна, то подключение к местоположению вторичной реплики в группе доступности завершится ошибкой в следующих случаях:  
  
1.  Если местоположение вторичных реплик не настроено для приема подключений.  
  
2.  Если приложение использует **applicationIntent=ReadWrite** (описано ниже) и расположение вторичных реплик настроено для доступа только для чтения.  
  
 При соединении произойдет ошибка, если первичная реплика настроена для отклонения рабочих нагрузок только для чтения, а строка подключения содержит **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Переход с зеркального отображения базы данных на использование кластеров с несколькими подсетями  
 При переводе приложения [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], которое сейчас использует зеркальное отображение базы данных, на сценарий с использованием множества подсетей необходимо удалить свойство подключения **failoverPartner**, заменив его свойством **multiSubnetFailover** со значением **true**, а имя сервера в строке подключения — прослушивателем группы доступности. Если в строке подключения используются **failoverPartner** и **multiSubnetFailover=true**, то драйвер выдаст ошибку. Но если в строке подключения используются параметры **failoverPartner** и **multiSubnetFailover=false** (или **ApplicationIntent=ReadWrite**), то приложение будет использовать зеркальное отображение базы данных.  
  
 Если зеркальное отображение базы данных применяется к базе данных-источнику группы доступности, то драйвер вернет ошибку. Это также произойдет при использовании параметра **multiSubnetFailover=true** в строке подключения, относящейся к базе данных-источнику, а не к прослушивателю группы доступности.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Новые методы, поддерживающие multiSubnetFailover и applicationIntent  
 Следующие методы обеспечивают программный доступ к **multiSubnetFailover**, **applicationIntent** и **transparentNetworkIPResolution** строки подключения ключевые слова:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 **GetMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** и **setTransparentNetworkIPResolution** также добавляются методы для [класса SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [ Класс SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), и [класс SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
## <a name="ssl-certificate-validation"></a>Проверка сертификатов SSL  
 Группа доступности состоит из нескольких физических серверов. В драйвер [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] добавлена поддержка **альтернативного имени субъекта** в SSL-сертификатах, что позволяет связать несколько узлов с одним сертификатом. Дополнительные сведения о протоколе SSL см. в разделе [Общие сведения о поддержке SSL](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
