---
title: Поддержка высокой доступности и аварийного восстановления в JDBC Driver
description: В этой статье представлены сведения о поддержке Microsoft JDBC Driver for SQL Server для высокой доступности и аварийного восстановления (группы доступности AlwaysOn).
ms.custom: ''
ms.date: 07/13/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3a79f3f47db8bfa048ecb5b910bcb4946cf7a7c
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301823"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Поддержка высокой доступности и аварийного восстановления в JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе рассматривается поддержка [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] высокой доступности с аварийным восстановлением ― [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Дополнительные сведения о среде [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]см. в электронной документации по [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 Начиная с версии 4.0 драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] в свойствах подключения можно указать прослушиватель группы доступности (высокой доступности и аварийного восстановления). Если приложение [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] подключается к базе данных Always On, которая выполняет отработку отказа, то первоначальное подключение разрывается и приложение должно открыть новое подключение, чтобы продолжить работу после обработки отказа. В версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] добавлены следующие [свойства подключения](setting-the-connection-properties.md):  
  
- **multiSubnetFailover**  
  
- **applicationIntent**

Укажите multiSubnetFailover=true при подключении к прослушивателю группы доступности или экземпляру отказоустойчивого кластера. Обратите внимание, что **multiSubnetFailover** по умолчанию имеет значение false. Используйте **applicationIntent**, чтобы объявить тип рабочей нагрузки приложения. Дополнительные сведения см. в разделах ниже.

Начиная с версии 6.0 Microsoft JDBC Driver for SQL Server, для прозрачного подключения к группе доступности Always On или к серверу с несколькими IP-адресами добавляется новое свойство соединения **transparentNetworkIPResolution** (TNIR). Если **transparentNetworkIPResolution** имеет значение true, драйвер пытается подключиться к первому доступному IP-адресу. Если первая попытка завершается неудачно, драйвер пытается подключиться ко всем IP-адресам параллельно до истечения времени ожидания, отменяя все ожидающие попытки подключения, когда один из них завершается успешно.

Обратите внимание на следующее.

- по умолчанию transparentNetworkIPResolution имеет значение true
- transparentNetworkIPResolution игнорируется, если multiSubnetFailover имеет значение true  
- transparentNetworkIPResolution игнорируется, если используется зеркальное отображение базы данных  
- transparentNetworkIPResolution игнорируется, если количество IP-адресов превышает 64.  
- Если transparentNetworkIPResolution имеет значение true, первая попытка соединения использует значение времени ожидания 500 мс. Остальные попытки подключения следуют той же логике, что и компонент multiSubnetFailover.  

> [!NOTE]
> Если вы используете Драйвер Microsoft JDBC версии 4.2 (или более ранней) для SQL Server и если **multiSubnetFailover** имеет значение false, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] пытается подключиться к первому IP-адресу. Если [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не может установить подключение к первому IP-адресу, то подключение завершается сбоем. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не будет повторять попытку подключения к другим IP-адресам, связанным с сервером.

> [!NOTE]
> Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  

## <a name="connecting-with-multisubnetfailover"></a>Подключение с помощью multiSubnetFailover  

 Всегда указывайте **MultiSubnetFailover=True** при соединении с прослушивателем группы доступности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **multiSubnetFailover** позволяет группам доступности и экземплярам отказоустойчивого кластера в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] быстрее выполнить отработку отказа, а также значительно сократить время перехода на другой ресурс для топологий AlwaysOn с одной подсетью или несколькими. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. При отработке отказа подсети [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет активно повторять попытки установить TCP-подключение.  
  
 Свойство подключения **multiSubnetFailover** указывает, что приложение развертывается в группе доступности или экземпляре отказоустойчивого кластера, а также что [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] попытается подключиться ко всем IP-адресам базы данных в первичном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда для подключения установлено свойство **MultiSubnetFailover=true**, клиент будет пытаться повторно установить TCP-подключение с более частым интервалом, чем заданные в операционной системе интервалы повторной отправки TCP-пакетов по умолчанию. Это поведение позволяет ускорить восстановление соединения после отработки отказа в группе доступности Always On или в экземпляре отказоустойчивого кластера Always On; метод может применяться к группам доступности и экземплярам отказоустойчивых кластеров как с одной, так и с несколькими подсетями.  
  
 Дополнительные сведения о ключевых словах строки подключения драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]см. в разделе [Настройка свойств подключения](setting-the-connection-properties.md).  
  
 Указание **multiSubnetFailover=true** при подключении к объекту, отличному от прослушивателя группы доступности или экземпляра отказоустойчивого кластера, может привести к снижению производительности и не поддерживается.  
  
 Если диспетчер безопасности не установлен, то виртуальная машина Java кэширует виртуальные IP-адреса (VIP) на ограниченный период времени (по умолчанию определяемый реализацией JDK и свойствами Java networkaddress.cache.ttl и networkaddress.cache.negative.ttl). Если диспетчер безопасности JDK установлен, то виртуальная машина Java будет кэшировать адреса VIP, причем кэш по умолчанию не обновляется. Необходимо установить «время существования» для кэша виртуальной машины Java (networkaddress.cache.ttl) в один день. Если этого не сделать, старые значения не будут исключаться из кэша виртуальной машины Java при добавлении или обновлении адресов VIP. Дополнительные сведения о networkaddress.cache.ttl и networkaddress.cache.negative.ttl см. в разделе [https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Следуйте приведенным ниже рекомендациям для подключения к серверу в группе доступности или экземпляру отказоустойчивого кластера.  
  
- Драйвер выдаст ошибку, если свойство соединения **instanceName** указано в той же строке подключения, что и свойство соединения **multiSubnetFailover**. Эта ошибка связана с тем, что браузер SQL Server в группе доступности не используется. Однако если также указано свойство подключения **portNumber**, драйвер будет игнорировать **instanceName** и использовать **portNumber**.  
  
- Используйте свойство подключения **multiSubnetFailover** при подключении к одной подсети или нескольким — это благоприятно скажется на производительности в любом случае.  
  
- Чтобы установить соединение с группой доступности, указывайте ее прослушиватель в строке подключения вместо сервера. Например, jdbc:sqlserver://VNN1.  
  
- При установлении соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], настроенным на работу с более чем 64 IP-адресами, будет возникать ошибка соединения.  
  
- Поведение приложения, использующего свойство подключения **multiSubnetFailover**, не зависит от типа аутентификации: проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], проверка подлинности Kerberos или проверка подлинности Windows.  
  
- Значение **loginTimeout** можно увеличить с учетом времени отработки отказа и для уменьшения количества попыток приложения повторно установить подключение.  
  
- Распределенные транзакции не поддерживаются.  
  
Если маршрутизация только для чтения неактивна, то подключение к местоположению вторичной реплики в группе доступности завершится ошибкой в следующих случаях:  
  
1. Если местоположение вторичных реплик не настроено для приема подключений.  
  
2. Если приложение использует **applicationIntent=ReadWrite** (описано ниже) и расположение вторичных реплик настроено для доступа только для чтения.  
  
При соединении произойдет ошибка, если первичная реплика настроена для отклонения рабочих нагрузок только для чтения, а строка подключения содержит **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Переход с зеркального отображения базы данных на использование кластеров с несколькими подсетями  

При переводе приложения [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], которое сейчас использует зеркальное отображение базы данных, на сценарий с использованием множества подсетей необходимо удалить свойство подключения **failoverPartner**, заменив его свойством **multiSubnetFailover** со значением **true**, а имя сервера в строке подключения — прослушивателем группы доступности. Если в строке подключения используются **failoverPartner** и **multiSubnetFailover=true**, то драйвер выдаст ошибку. Но если в строке подключения используются параметры **failoverPartner** и **multiSubnetFailover=false** (или **ApplicationIntent=ReadWrite**), то приложение будет использовать зеркальное отображение базы данных.  
  
Если зеркальное отображение базы данных применяется к базе данных-источнику группы доступности, то драйвер вернет ошибку. Это также произойдет при использовании параметра **multiSubnetFailover=true** в строке подключения, относящейся к базе данных-источнику, а не к прослушивателю группы доступности.  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]

## <a name="connection-pooling"></a>Организация пулов соединений

При использовании драйвера Microsoft JDBC для SQL Server в сочетании с библиотекой пулов соединений следует учитывать следующие моменты.

- Если настроена маршрутизация только для чтения и пул серверов, доступных только для чтения, для которых требуется распределить нагрузку, пул подключений уменьшит число возможностей для новых подключений, которые будут распределены по целевым серверам.
- Чтобы избежать более высокой нагрузки на один сервер в пуле, выберите параметры пула, которые допускают равномерное распределение подключений в пуле.
- Убедитесь, что для пула подключений настроено время существования соединения. Если реплика только для чтения недоступна, когда осуществляется подключение только для чтения, то конфигурация должна гарантировать, что подключение в конечном итоге будет закрыто и повторно установлено к реплике только для чтения, когда она снова станет доступной.

## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Новые методы, поддерживающие multiSubnetFailover и applicationIntent  

Следующие методы предоставляют программный доступ к ключевым словам строки подключения **multiSubnetFailover**, **applicationIntent** и **transparentNetworkIPResolution**.  
  
- [SQLServerDataSource.getApplicationIntent](reference/getapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setApplicationIntent](reference/setapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.getMultiSubnetFailover](reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setMultiSubnetFailover](reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDriver.getPropertyInfo](reference/getpropertyinfo-method-sqlserverdriver.md)  

- SQLServerDataSource.setTransparentNetworkIPResolution

- SQLServerDataSource.getTransparentNetworkIPResolution
  
Методы **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** и **setTransparentNetworkIPResolution** также добавляются в классы [SQLServerDataSource](reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](reference/sqlserverconnectionpooldatasource-class.md) и [SQLServerXADataSource](reference/sqlserverxadatasource-class.md).  
  
## <a name="tlsssl-certificate-validation"></a>Проверка TLS/SSL-сертификатов  

Группа доступности состоит из нескольких физических серверов. В драйвер [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] добавлена поддержка **альтернативного имени субъекта** в TLS/SSL-сертификатах, что позволяет связать несколько узлов с одним сертификатом. Дополнительные сведения о TLS см. в разделе [Основные сведения о поддержке шифрования](understanding-ssl-support.md).  
  
## <a name="see-also"></a>См. также раздел  

[Подключение к SQL Server с помощью JDBC Driver](connecting-to-sql-server-with-the-jdbc-driver.md)  
[Настройка свойств подключения](setting-the-connection-properties.md)  
