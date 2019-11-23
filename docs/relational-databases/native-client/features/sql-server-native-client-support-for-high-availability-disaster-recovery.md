---
title: SQL Server Native Client поддержка высокого уровня доступности, аварийного восстановления | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2b06186b-4090-4728-b96b-90d6ebd9f66f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7cf7313c127be38e72131c604c4880963242ed3
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73788033"
---
# <a name="sql-server-native-client-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе описывается поддержка Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения о [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделах [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Создание и настройка групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) и [Активные вторичные реплики. Доступ только для чтения ко вторичным репликам (группы доступности AlwaysOn)](~/database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 Прослушиватель для заданной группы доступности можно задать в строке подключения. Если приложение Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подключено к базе данных в группе доступности, которая выполняет переход на другой ресурс, то исходное соединение является разорванным, а приложение должно установить новое соединение, чтобы продолжить работу после отработки отказа.  
  
 Если соединение с прослушивателем группы доступности не будет установлено, а с именем узла связано несколько IP-адресов, то собственный клиент Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] последовательно переберет все IP-адреса, связанные с записью DNS. Это может занять много времени, если первый IP-адрес, возвращенный DNS-сервером, не привязан ни к одной из сетевых интерфейсных плат. При установлении соединения с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client пытается установить соединения со всеми IP-адресами параллельно. Если одна из попыток соединения завершается успешно, то все остальные производимые попытки соединения отменяются.  
  
> [!NOTE]  
>  Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  
  
## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover  
 При установлении соединения с прослушивателем группы доступности SQL Server 2012 или экземпляром отказоустойчивого кластера SQL Server 2012 всегда необходимо указывать **MultiSubnetFailover=Yes**. **MultiSubnetFailover** обеспечивает более быструю отработку отказа для всех групп доступности и экземпляра отказоустойчивого кластера в SQL Server 2012 и значительно сокращает время отработки отказа для одноAlways Onных топологий с одной и несколькими подсетями. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. Во время отработки отказа в подсети собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет активно выполнять попытки повторного TCP-соединения.  
  
 Свойство соединения **MultiSubnetFailover** указывает, что приложение развертывается в группе доступности или на экземпляре отказоустойчивого кластера, а также что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client выполнит попытку соединения с базой данных в первичном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], попытавшись установить соединение со всеми IP-адресами группы доступности. Когда для соединения установлено свойство **MultiSubnetFailover=Yes**, то клиент производит повторные попытки установить TCP-соединение быстрее интервалов повторной отправки TCP-пакетов по умолчанию для операционной системы. Это обеспечивает более быстрое повторное подключение после отработки отказа Always On группы доступности или экземпляра отказоустойчивого кластера Always On и применяется к группам доступности с одним и несколькими подсетями и к экземплярам отказоустойчивого кластера.  
  
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


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


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
  
|Функция|Описание|  
|--------------|-----------------|  
|[SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)|Список серверов, возвращаемый **SQLBrowseConnect**, не содержит имен виртуальных сетей. Будет отображен только список серверов без указания того, является ли сервер отдельным, сервером-источником или сервером-получателем в отказоустойчивом кластере, в котором содержатся два экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенные для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], или более. При возникновении ошибки подключения к серверу причина может заключаться в несоответствии параметра **ApplicationIntent** конфигурации сервера.<br /><br /> Поскольку **SQLBrowseConnect** не распознает серверы в отказоустойчивых кластерах, содержащих два или более экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые были включены для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], **SQLBrowseConnect** не учитывает ключевое слово строки подключения **MultiSubnetFailover**.|  
|[SQLConnect](../../../relational-databases/native-client-odbc-api/sqlconnect.md)|**SQLConnect** поддерживает как **ApplicationIntent**, так и **MultiSubnetFailover** через имя источника данных (DSN) или свойства соединения.|  
|[SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)|**SQLDriverConnect** поддерживает **ApplicationIntent** и **MultiSubnetFailover** через ключевые слова строки подключения, свойства соединения или имя DSN.|  
  
## <a name="ole-db"></a>OLE DB  
 OLE DB в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client не поддерживает ключевое слово **MultiSubnetFailover**.  
  
 OLE DB в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает назначение приложения. Для назначений приложений OLE DB будет поддерживаться тот же режим, что и для приложений ODBC (см. выше).  
  
 В собственном клиенте [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] было добавлено одно ключевое слово строки подключения OLE DB:  
  
-   **Application Intent**  
  
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
  
## <a name="see-also"></a>См. также статью  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Использование ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
  
