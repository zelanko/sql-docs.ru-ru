---
title: Параллельное хранилище данных компонентов - Analytics Platform System | Документация Майкрософт
description: В этой статье объясняется, программное обеспечение устройства и компоненты программного обеспечения не является специализированным Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: aaf90124cc7877b633a997a2c4f170057b965028
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510932"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Параллельное хранилище данных компонентов - Analytics Platform System
В этой статье объясняется, программное обеспечение устройства и компоненты программного обеспечения не является специализированным Analytics Platform System.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Параллельное хранилище данных программного обеспечения](media/parallel-data-warehouse-software.png "программного обеспечения Parallel Data Warehouse")  
  
## <a name="sec1"></a>Программное обеспечение устройства - запрос, обработка и хранение данных пользователя  
  
### <a name="control-node"></a>Управляющий узел  
Механизм MPP  
Механизм MPP является центром системы массовую параллельную обработку (MPP). Он выполняет следующие действия:  
  
-   Создает планы параллельных запросов и координирует параллельного выполнения запросов на вычислительных узлах.  
  
-   Сохраняет и координирует метаданные и данные конфигурации для всех баз данных.  
  
-   Управляет базы данных SQL Server PDW проверки подлинности и авторизации.  
  
-   Отслеживает состояние оборудования и программного обеспечения.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) является частью «секретным ингредиентом» PDW. Он выполняет следующие действия:  
  
-   Передает данные в и из узлов SQL Server PDW.  
  
-   Процессы запроса операции, требующие передачи данных между узлами.  
  
-   Повышает производительность запросов путем оптимизации скорости передачи данных.  
  
### <a name="admin-console"></a>Консоль администрирования  
Консоль администратора служит веб-приложения, которая представляет состояние устройства, работоспособность и сведения о производительности.  
  
### <a name="configuration-manager"></a>диспетчер конфигураций  
Configuration Manager (dwconfig.exe), — это средство, которое Администраторы устройств используйте для настройки Analytics Platform System.  
  
### <a name="control-node-databases"></a>Базы данных узла управления  
SQL Server управляет всеми базами данных на узел элемента управления.  
  
-   Базе данных оболочки, который управляет метаданными для всех распределенных пользовательских баз данных.  
  
-   Базы данных TempDB содержит метаданные для всех временных таблиц пользователя на устройстве.  
  
-   Мастер — главная таблица для SQL Server на узле управления.  
  
### <a name="compute-node"></a>Вычислительный узел  
Вычислительные узлы также являются параллельной обработки данных и единицах хранения. У них непосредственно подключенное хранилище и использовать SQL Server для управления данными пользователя.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) выполняется на каждом вычислительном узле, выполнив следующие действия:  
  
-   В ходе обработки параллельных запросов DMS передачи данных из других узлов компьютера и в управляющем узле.  
  
-   DMS, на каждом вычислительном узле, получает загрузки данных в параллельном режиме. Данные загружаются в параллельном режиме непосредственно с сервера загрузки на вычислительных узлах  
  
-   DMS передает данные в каждом вычислительном узле непосредственно на сервер резервного копирования.  
  
-   С помощью PolyBase, DMS передает данные и внешнем кластере Hadoop или хранилища Blob.  
  
### <a name="compute-node-databases"></a>Вычисления узел баз данных 
Каждый вычислительный узел запущен экземпляр служб SQL Server для обработки запросов и управления данными пользователя.  
  
## <a name="appliance-fabric"></a>Fabric устройства  
Fabric устройство предоставляет операционной системы и службы инфраструктуры сети для устройства.  
  
### <a name="domain-controller"></a>Контроллер домена  
Доменных служб Active Directory (AD) (DS)  
Система Analytics Platform System выполняет проверку подлинности между узлами Analytics Platform System и управляет проверкой подлинности имен входа проверки подлинности Windows для SQL Server PDW.  
  
Служба DNS  
Службы доменных имен (DNS) Windows разрешается доменные имена в IP-адреса для Analytics Platform System appliance.  
  
### <a name="windows-deployment-service"></a>Службы развертывания Windows  
Службы развертывания Windows (WDS) развертывания операционной системы Windows Server на устройство. Оно развертывается на каждом узле и виртуальной машины на устройстве.  
  
Служба DHCP создает IP-адреса узлов в рамках домена устройство может подключиться к сети устройства без необходимости предварительно настроенные IP-адрес.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Система Analytics Platform System использует виртуализацию для обеспечения высокой доступности. Virtual Machine Manager размещает System Center для развертывания операционной системы на физических узлах.  
  
Windows Server Update Services (WSUS) для применения или удаления обновления Windows для всех узлов и виртуальных машин.  
  
### <a name="windows-server"></a>Windows Server  
Все узлы и виртуальные машины в устройстве запуска операционной системы Windows Server.  
  
### <a name="failover-clustering"></a>Отказоустойчивая кластеризация  
Отказоустойчивая кластеризация Windows предоставляет возможность перезапуска процессов на пассивном узле в случае, если узел выйдет из строя.  
  
### <a name="storage-spaces"></a>Дисковые пространства  
Дисковые пространства Windows управляет данными пользователя как пул носителей для небольшой группы вычислительных узлов. В случае сбоя узла вычислений, данных, по-прежнему доступен через дополнительный вычислительный узел в группе.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server предоставляет простое и надежное решение виртуализации. Система Analytics Platform System использует виртуализации для распределения ресурсов ЦП и для обеспечения высокой доступности для узлов PDW и устройства компоненты структуры.  
  
## <a name="sec2"></a>Нереляционные данные
Технология PolyBase объединяет данные SQL Server PDW с внешними данными Hadoop. Данные Hadoop могут храниться на любой из этих источников данных Hadoop:  
  
-   Распределение Hortonworks Hadoop  
  
-   Распределение Cloudera Hadoop  
  
-   HDInsight данные, хранящиеся в больших двоичных объектов хранилища Azure  
  
## <a name="query-tools"></a>Средства запросов   
  
Запросы пишутся с Transact\-SQL изменено в соответствии с MPP характер запросов. Все запросы отправляются к управляющему узлу, который создает параллельный план запроса для выполнения запроса на вычислительные узлы.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools выполняется внутри Visual Studio и является нашей рекомендуемое средство графического пользовательского интерфейса для отправки запросов к SQL Server PDW. Это похоже на SQL Server Management Studio, позволяя переходить между обозреватель объектов.  
  
Если у вас нет Visual Studio, можно загрузить бесплатно нужные инструменты. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>sqlcmd средство командной строки запроса  
sqlcmd — это средство командной строки SQL Server для запуска Transact\-SQL инструкции и системные команды. Он работает с SQL Server PDW и наши рекомендуемое средство командной строки для выполнения запросов к SQL Server PDW. С помощью sqlcmd запуском Transact\-инструкций SQL в интерактивном режиме из командной строки, как пакетный файл, или с помощью Windows PowerShell.  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Службы Integration Services  
Службы Integration Services можно использовать для запроса SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Linked Server  
С помощью подключения к серверу SQL Server связаны, можно использовать SQL Server для отправки Transact\-инструкции SQL для SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Средства бизнес-аналитики
  
### <a name="analysis-services"></a>Службы Analysis Services  
SQL Server PDW — это допустимый источник данных для базы данных служб Analysis Services и PowerPivot для Excel модели. С помощью поставщика OLE DB, можно настроить куб служб Analysis Services для использования многомерных оперативная аналитическая обработка (MOLAP) или хранилища реляционная интерактивная аналитическая обработка (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>построитель отчетов  
SQL Server PDW можно использовать как источник данных SQL Server для отчетов, разработанных для служб Reporting Services с помощью построителя отчетов SQL Server. Также можно использовать SQL Server PDW как источник SQL Server для моделей отчетов. С помощью диспетчера отчетов или на сервере отчетов API, можно создать модель из базы данных SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot для Excel  
Можно подключаться к SQL Server PDW с PowerPivot для Excel, бесплатной загрузки, который значительно расширяет возможности анализа данных Excel.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Загрузка средств 
  
### <a name="integration-services"></a>Службы Integration Services  
Установите PDW назначения адаптеры, которые позволяют использовать службы ServerIntegration SQL для загрузки данных в SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader загрузчика командной строки  
dwloader — это средство командной строки загрузки, который загружает данные в параллельном режиме с сервера загрузки в SQL Server PDW вычислительные узлы. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase для интеграции Hadoop  
Технология PolyBase можно загрузить на нереляционные данные от кластера Hadoop в реляционной таблице в SQL Server PDW. Данные Hadoop может размещаться в кластере Hadoop внешних или в большом двоичном объекте хранилища Azure.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Резервное копирование базы данных и восстановление  
SQL Server PDW использует резервную копию базы данных Transact-SQL и восстановление команд для резервного копирования и восстановления пользовательских баз данных, в параллельном режиме и из резервной копии сервера. SQL Server PDW записывает резервные копии в каталог, в общую папку Windows, а затем точно так же восстанавливает данные из общей папки Windows.  
  
Дополнительные сведения см. в разделе [Планирование резервного копирования и загрузки оборудования](backup-and-loading-hardware.md) и [резервное копирование и восстановление: Обзор](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Копирование удаленных таблиц  
Копирование удаленной таблицы позволяет копирование таблиц из базы данных SQL Server PDW в удаленных базах данных SMP SQL Server (не являющийся устройством). Это позволяет реализовать сценарии звездообразной для SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Наблюдение  
Система Analytics Platform System имеет несколько способов для отслеживания активности устройства  
  
### <a name="admin-console"></a>Консоль администрирования  
Консоль администратора позволяет просматривать текущее состояние о работоспособности устройства. Это выполняется как веб-приложения на узле управления и доступен по протоколу https.  
  
Дополнительные сведения см. в разделе [мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Системные представления  
В консоли администрирования зависит от системы Просмотр запросов. Вы можете запрашивать системные представления по отдельности, чтобы получить конкретные сведения, необходимые.  

Дополнительные сведения см. в разделе [мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Существуют пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. 

Чтобы настроить устройство для SCOM, см. в разделе [мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
