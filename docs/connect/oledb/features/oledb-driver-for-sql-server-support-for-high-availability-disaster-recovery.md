---
title: Драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления | Документы Microsoft
description: Драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dc6bba3823e1683baa7962bd11889fbaca83dea4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>Драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой статье описывается драйвер OLE DB для поддержки SQL Server (добавлено в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения о [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделах [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Создание и настройка групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) и [Активные вторичные реплики. Доступ только для чтения ко вторичным репликам (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 Прослушиватель для заданной группы доступности можно задать в строке подключения. Если драйвер OLE DB для приложения SQL Server подключен к базе данных в группе доступности, которая выполняет отработку отказа, то исходное соединение разрывается и приложение должно установить новое соединение для продолжения работы после отработки отказа.  
  
 Если вы не подключаетесь к прослушивателю группы доступности и несколько IP-адресов связаны с именем узла, драйвер OLE DB для SQL Server будет поочередно для всех IP-адресов, ассоциированных с записью DNS. Это может занять много времени, если первый IP-адрес, возвращенный DNS-сервером, не привязан ни к одной из сетевых интерфейсных плат. При подключении к прослушивателю группы доступности драйвер OLE DB для SQL Server пытается установить соединения для всех IP-адресов в параллельном режиме, и если попытка соединения завершается успешно, то драйвер отменяет любые попытки ожидания соединения.  
  
> [!NOTE]  
> Увеличение времени ожидания соединения и реализация логики повторного соединения позволяют повысить вероятность соединения приложения с группой доступности. Кроме того, в связи с возможностью неудачного подключения при отработке отказа группы доступности следует реализовать логику повторного соединения, обеспечивающую неограниченное число попыток соединения до достижения успеха.  
  
## <a name="connecting-with-multisubnetfailover"></a>Соединение с помощью MultiSubnetFailover  
 Всегда указывайте **MultiSubnetFailover = Yes** при подключении к прослушивателю SQL Server группы доступности AlwaysOn или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра отказоустойчивого кластера. **MultiSubnetFailover** обеспечивает ускоренную отработку отказа для всех групп доступности AlwaysOn и экземпляров отказоустойчивых кластеров в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]и значительно уменьшит время отработки отказа для одной или несколькими подсетями топологий Always On. При отработке отказа с в нескольких подсетях клиент будет выполнять попытки соединения параллельно. При отработке отказа драйвер OLE DB для SQL Server будет повторять попытки соединения по протоколу TCP.  
  
 **MultiSubnetFailover** свойство соединения указывает, что приложение развертывается в группе доступности или экземпляра отказоустойчивого кластера и что драйвер OLE DB для SQL Server попытается соединиться с базой данных на основной [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, пытаясь подключиться ко всем IP-адресов. Когда для соединения установлено свойство **MultiSubnetFailover=Yes**, то клиент производит повторные попытки установить TCP-соединение быстрее интервалов повторной отправки TCP-пакетов по умолчанию для операционной системы. Это позволяет ускорить восстановление соединения после отработки отказа группы доступности AlwaysOn или экземпляра отказоустойчивого кластера и применимы к одним и несколькими подсетями группы доступности и экземпляров отказоустойчивых кластеров.  
  
 Дополнительные сведения о ключевых словах строки соединения см. в разделе [с помощью ключевых слов строки подключения с драйвер OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
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
  
Если обновить драйвер OLE DB для SQL Server приложения, использующего зеркальное отображение базы данных в сценарии с несколькими подсетями, следует удалить **Failover_Partner** свойства соединения и замените ее на  **MultiSubnetFailover** значение **Да** и заменить имя сервера в строке соединения с прослушивателем группы доступности. Если в строке подключения используются **Failover_Partner** и **MultiSubnetFailover=Yes**, то драйвер выдаст ошибку. Но если в строке подключения используются параметры **Failover_Partner** и **MultiSubnetFailover=No** (или **ApplicationIntent=ReadWrite**), то приложение будет использовать зеркальное отображение базы данных.  
  
Если в базе данных-источнике группы доступности используется зеркальное отображение баз данных, то драйвер вернет ошибку. Это также произойдет в том случае, если используется параметр **MultiSubnetFailover=Yes** в строке подключения, устанавливающей соединение с базой данных-источником, а не с прослушивателем группы доступности.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="ole-db"></a>OLE DB  
Драйвер OLE DB для SQL Server поддерживает как **ApplicationIntent** и **MultiSubnetFailover** ключевые слова.   
  
Были добавлены два ключевых слов строки подключения OLE DB для поддержки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в драйвер OLE DB для SQL Server:  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 Дополнительные сведения о ключевых словах строки подключения в драйвер OLE DB для SQL Server см. в разделе [с помощью ключевых слов строки подключения с драйвер OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

### <a name="application-intent"></a>Назначение приложения 

Эквивалентными свойствами соединения являются следующие:  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
Драйвер OLE DB для SQL Server приложения можно использовать один из способов для указания назначения приложения:  
  
 -   **IDBInitialize::Initialize**  
 **IDBInitialize::Initialize** использует ранее настроенный набор свойств для инициализации источника данных и создания объекта источника данных. Укажите назначение приложения в качестве свойства поставщика или в виде расширенной строки свойств.  
  
 -   **IDataInitialize::GetDataSource**  
 **IDataInitialize::GetDataSource** принимает строку подключения, которая может содержать ключевое слово **Application Intent**.  
  
 -   **IDBProperties::SetProperties**  
 Чтобы задать значение свойства **ApplicationIntent**, вызовите **IDBProperties::SetProperties**, передав свойство **SSPROP_INIT_APPLICATIONINTENT** со значением "**ReadWrite**" или "**ReadOnly**" или свойство **DBPROP_INIT_PROVIDERSTRING** со значением, содержащим "**ApplicationIntent=ReadOnly**" или "**ApplicationIntent=ReadWrite**".  
  
Назначение приложения можно указать в поле "Свойства назначения приложения" на вкладке "Все" в диалоговом окне **Свойства канала передачи данных**.  
  
После установки неявных соединений эти подключения будут использовать настройку назначения приложения для родительского подключения. Аналогичным образом несколько сеансов, созданных с использованием одного источника данных, будут наследовать настройки назначения приложения от источника данных.  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

Эквивалентными свойствами соединения являются следующие:  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  

Драйвер OLE DB для SQL Server приложения можно использовать один из следующих методов для задания параметра MultiSubnetFailover:  

 -   **IDBInitialize::Initialize**  
 **IDBInitialize::Initialize** использует ранее настроенный набор свойств для инициализации источника данных и создания объекта источника данных. Укажите назначение приложения в качестве свойства поставщика или в виде расширенной строки свойств.  
  
 -   **IDataInitialize::GetDataSource**  
 **IDataInitialize::GetDataSource** принимает строку подключения, которая может содержать **MultiSubnetFailover** ключевое слово.  

-   **IDBProperties::SetProperties**  
Чтобы задать **MultiSubnetFailover** значение свойства, вызовите **IDBProperties::SetProperties** передав **SSPROP_INIT_MULTISUBNETFAILOVER** свойство со значением  **VARIANT_TRUE** или **VARIANT_FALSE** или **DBPROP_INIT_PROVIDERSTRING** свойство которых содержит значение «**MultiSubnetFailover = Yes** «или»**MultiSubnetFailover = нет**».

#### <a name="example"></a>Пример

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```

## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для компонентов SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
