---
title: "Поддержка собственного клиента SQL Server для высокого уровня доступности и аварийного восстановления | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2b06186b-4090-4728-b96b-90d6ebd9f66f
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1940375cc3d822d994c673d965e1fb7e23385596
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-native-client-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В этом разделе описывается поддержка Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения о [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделах [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Создание и настройка групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) и [Активные вторичные реплики. Доступ только для чтения ко вторичным репликам (группы доступности AlwaysOn)](~/database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 Прослушиватель для заданной группы доступности можно задать в строке подключения. Если приложение Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подключено к базе данных в группе доступности, которая выполняет переход на другой ресурс, то исходное соединение является разорванным, а приложение должно установить новое соединение, чтобы продолжить работу после отработки отказа.  
  
 Если соединение с прослушивателем группы доступности не будет установлено, а с именем узла связано несколько IP-адресов, то собственный клиент Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] последовательно переберет все IP-адреса, связанные с записью DNS. Это может занять много времени, если первый IP-адрес, возвращенный DNS-сервером, не привязан ни к одной из сетевых интерфейсных плат. При установлении соединения с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client пытается установить соединения со всеми IP-адресами параллельно. Если одна из попыток соединения завершается успешно, то все остальные производимые попытки соединения отменяются.  
  
> [!NOTE]  
>  Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  
  
## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover  
 При установлении соединения с прослушивателем группы доступности SQL Server 2012 или экземпляром отказоустойчивого кластера SQL Server 2012 всегда необходимо указывать **MultiSubnetFailover=Yes**. **MultiSubnetFailover** обеспечивает ускоренную отработку отказа для всех групп доступности и отказоустойчивого кластера экземпляра SQL Server 2012 и значительно уменьшит время отработки отказа для одной или несколькими подсетями топологий Always On. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. Во время отработки отказа в подсети собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет активно выполнять попытки повторного TCP-соединения.  
  
 Свойство соединения **MultiSubnetFailover** указывает, что приложение развертывается в группе доступности или на экземпляре отказоустойчивого кластера, а также что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client выполнит попытку соединения с базой данных в первичном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], попытавшись установить соединение со всеми IP-адресами группы доступности. Когда для соединения установлено свойство **MultiSubnetFailover=Yes**, то клиент производит повторные попытки установить TCP-соединение быстрее интервалов повторной отправки TCP-пакетов по умолчанию для операционной системы. Это позволяет ускорить восстановление соединения после отработки отказа группы доступности AlwaysOn или всегда в экземпляр отказоустойчивого кластера и применимы к одним и несколькими подсетями группы доступности и экземпляров отказоустойчивых кластеров.  
  
 Дополнительные сведения о ключевых словах строки подключения см. в статье [Использование ключевых слов строки подключения с SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Указание параметра **MultiSubnetFailover=Yes** при соединении с объектом, отличным от прослушивателя группы доступности или экземпляра отказоустойчивого кластера, может привести к снижению производительности и не поддерживается.  
  
 Следуйте приведенным ниже рекомендациям для подключения к серверу в группе доступности или экземпляру отказоустойчивого кластера.  
  
-   Пользуйтесь свойством соединения **MultiSubnetFailover** при установлении соединения с одной или несколькими подсетями, это благоприятно скажется на производительности в любом случае.  
  
-   Чтобы установить соединение с группой доступности, указывайте ее прослушиватель в строке подключения вместо сервера.  
  
-   При установлении соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], настроенным на работу с более чем 64 IP-адресами, будет возникать ошибка соединения.  
  
-   Режим работы приложения, использующего свойство соединения **MultiSubnetFailover**, не зависит от типа проверки подлинности — [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], Kerberos или Windows.  
  
-   Значение **loginTimeout** можно увеличить с учетом времени отработки отказа, это уменьшит количество попыток повторного соединения в приложении.  
  
-   Распределенные транзакции не поддерживаются.  
  
 Если маршрутизация только для чтения неактивна, то подключение к местоположению вторичной реплики в группе доступности завершится ошибкой в следующих случаях:  
  
1.  Если местоположение вторичных реплик не настроено для приема подключений.  
  
2.  Если приложение использует **ApplicationIntent=ReadWrite** (описано ниже) и расположение вторичных реплик настроено для доступа только для чтения.  
  
 При соединении произойдет ошибка, если первичная реплика настроена для отклонения рабочих нагрузок только для чтения, а строка подключения содержит **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Переход с зеркального отображения базы данных на использование кластеров с несколькими подсетями  
 Если в строке подключения содержатся ключевые слова **MultiSubnetFailover** и **Failover_Partner**, то при соединении произойдет ошибка. Ошибка возникает также в том случае, если используется **MultiSubnetFailover** и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает ответ партнера по обеспечению отработки отказа, указывающий на то, что он является частью пары зеркальных баз данных.  
  
 При обновлении приложения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, которое сейчас использует зеркальное отображение базы данных, до сценария с использованием нескольких подсетей необходимо удалить свойство соединения **Failover_Partner**, заменив его свойством **MultiSubnetFailover** со значением **Yes**, а имя сервера в строке подключения — прослушивателем группы доступности. Если в строке подключения используются **Failover_Partner** и **MultiSubnetFailover=Yes**, то драйвер выдаст ошибку. Но если в строке подключения используются параметры **Failover_Partner** и **MultiSubnetFailover=No** (или **ApplicationIntent=ReadWrite**), то приложение будет использовать зеркальное отображение базы данных.  
  
 Если в базе данных-источнике группы доступности используется зеркальное отображение баз данных, то драйвер вернет ошибку. Это также произойдет в том случае, если используется параметр **MultiSubnetFailover=Yes** в строке подключения, устанавливающей соединение с базой данных-источником, а не с прослушивателем группы доступности.  
  
## <a name="specifying-application-intent"></a>Задание намерения приложения  
 Когда **ApplicationIntent = ReadOnly**, клиент запрашивает рабочую нагрузку чтения при подключении к базе данных всегда включен. Сервер принудительно реализует намерение в момент соединения и во время выполнения инструкции USE database, но только в базе данных с поддержкой Always On.  
  
 Ключевое слово **ApplicationIntent** не работает с базами данных прежних версий, доступными только для чтения.  
  
 Базы данных можно разрешить или запретить рабочую нагрузку чтения для целевой базы данных Always On. (Это выполняется с использованием предложения **ALLOW_CONNECTIONS** инструкций **PRIMARY_ROLE** и **SECONDARY_ROLE**[!INCLUDE[tsql](../../../includes/tsql-md.md)].)  
  
 Ключевое слово **ApplicationIntent** служит для включения маршрутизации только для чтения.  
  
## <a name="read-only-routing"></a>Маршрутизация только для чтения  
 Маршрутизация только для чтения — это функция, которая может обеспечить доступность реплики базы данных, доступной только для чтения. Включение маршрутизации только для чтения  
  
1.  Необходимо установить соединение с прослушивателем группы доступности Always On.  
  
2.  Ключевое слово строки подключения **ApplicationIntent** должно быть установлено в значение **ReadOnly**.  
  
3.  Группа доступности должна быть настроена администратором базы данных на поддержку маршрутизации только для чтения.  
  
 Возможно, что не все из нескольких соединений, использующих маршрутизацию только для чтения, будут подключаться к одной и той же реплике только для чтения. Изменения в синхронизации баз данных или в конфигурации маршрутизации сервера могут привести к тому, что клиент будет подключаться к различным репликам только для чтения. Чтобы гарантировать, что все запросы на подключение только для чтения будут соединяться с одной и той же репликой только для чтения, не указывайте прослушиватель группы доступности в ключевом слове строки подключения **Server**. Вместо этого укажите имя экземпляра, доступного только для чтения.  
  
 На маршрутизацию только для чтения может потребоваться больше времени, чем на подключение к первичной реплике, поскольку маршрутизация только для чтения предусматривает прежде всего подключение к первичной реплике, а затем поиск наиболее подходящей доступной для чтения вторичной реплики. Учитывая этот факт, следует увеличить время ожидания входа в систему.  
  
## <a name="odbc"></a>интерфейс ODBC  
 Для поддержки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в собственном клиенте Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] были добавлены два ключевых слова строки подключения ODBC:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
 Дополнительные сведения о ключевых словах строки подключения ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client см. в статье [Использование ключевых слов строки подключения с SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Эквивалентными свойствами соединения являются следующие:  
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
 Дополнительные сведения о свойствах соединений ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client см. в разделе [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Возможность использования ключевых слов **ApplicationIntent** и **MultiSubnetFailover** будет доступна в администраторе источников данных ODBC для имен DSN, который использует драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 Приложение собственного клиента ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для создания соединения может использовать одну из трех функций.  
  
|Компонент|Description|  
|--------------|-----------------|  
|[SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)|Список серверов, возвращаемый **SQLBrowseConnect**, не содержит имен виртуальных сетей. Будет отображен только список серверов без указания того, является ли сервер отдельным, сервером-источником или сервером-получателем в отказоустойчивом кластере, в котором содержатся два экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенные для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], или более. При возникновении ошибки подключения к серверу причина может заключаться в несоответствии параметра **ApplicationIntent** конфигурации сервера.<br /><br /> Поскольку **SQLBrowseConnect** не распознает серверы в отказоустойчивых кластерах, содержащих два или более экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые были включены для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], **SQLBrowseConnect** не учитывает ключевое слово строки подключения **MultiSubnetFailover**.|  
|[SQLConnect](../../../relational-databases/native-client-odbc-api/sqlconnect.md)|**SQLConnect** поддерживает как **ApplicationIntent** , так и **MultiSubnetFailover** через имя источника данных (DSN) или свойства соединения.|  
|[SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)|**SQLDriverConnect** поддерживает **ApplicationIntent** и **MultiSubnetFailover** через ключевые слова строки подключения, свойства соединения или имя DSN.|  
  
## <a name="ole-db"></a>OLE DB  
 OLE DB в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client не поддерживает ключевое слово **MultiSubnetFailover**.  
  
 OLE DB в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает назначение приложения. Для назначений приложений OLE DB будет поддерживаться тот же режим, что и для приложений ODBC (см. выше).  
  
 В собственном клиенте [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] было добавлено одно ключевое слово строки подключения OLE DB:  
  
-   **Назначение приложения**  
  
 Дополнительные сведения о ключевых словах строки подключения в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client см. в статье [Использование ключевых слов строки подключения с SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Эквивалентными свойствами соединения являются следующие:  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
 В приложении собственного клиента OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для указания назначения приложения может использоваться один из следующих методов.  
  
 **IDBInitialize::Initialize**  
 **IDBInitialize::Initialize** использует ранее настроенный набор свойств для инициализации источника данных и создания объекта источника данных. Укажите назначение приложения в качестве свойства поставщика или в виде расширенной строки свойств.  
  
 **IDataInitialize::GetDataSource**  
 **IDataInitialize::GetDataSource** принимает строку подключения, которая может содержать ключевое слово **Application Intent**.  
  
 **IDBProperties::GetProperties**  
 **IDBProperties::GetProperties** получает значение свойства, которое в настоящее время задано для источника данных.  Значение **Application Intent** можно получить с помощью свойств DBPROP_INIT_PROVIDERSTRING и SSPROP_INIT_APPLICATIONINTENT.  
  
 **IDBProperties::SetProperties**  
 Чтобы задать значение свойства **ApplicationIntent**, вызовите **IDBProperties::SetProperties**, передав свойство **SSPROP_INIT_APPLICATIONINTENT** со значением "**ReadWrite**" или "**ReadOnly**" или свойство **DBPROP_INIT_PROVIDERSTRING** со значением, содержащим "**ApplicationIntent=ReadOnly**" или "**ApplicationIntent=ReadWrite**".  
  
 Назначение приложения можно указать в поле "Свойства назначения приложения" на вкладке "Все" в диалоговом окне **Свойства канала передачи данных**.  
  
 После установки неявных соединений эти подключения будут использовать настройку назначения приложения для родительского подключения. Аналогичным образом несколько сеансов, созданных с использованием одного источника данных, будут наследовать настройки назначения приложения от источника данных.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Использование ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
  
