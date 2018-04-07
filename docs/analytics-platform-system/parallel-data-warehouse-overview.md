---
title: Общие сведения о параллельного хранилища данных
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: В этом разделе описывается программное обеспечение устройства и компоненты программного обеспечения не является специализированным Analytics Platform System.
ms.date: 01/05/2017
ms.topic: article
ms.assetid: db0c4a43-a66d-4c44-ab91-791c5785f71c
caps.latest.revision: 20
ms.openlocfilehash: 42fb92c30c0487603f2ad8e870886f25b4c1655a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="parallel-data-warehouse-overview"></a>Общие сведения о параллельного хранилища данных
В этом разделе описывается программное обеспечение устройства и компоненты программного обеспечения не является специализированным Analytics Platform System.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Параллельное хранилище данных программного обеспечения](media/parallel-data-warehouse-software.png "программного обеспечения параллельного хранилища данных")  
  
## <a name="sec1"></a>Программное обеспечение устройства – запросов обработки и хранения данных пользователей  
  
### <a name="control-node"></a>Узел элемента управления  
Обработчик MPP  
Обработчик MPP является центром системы расширенной параллельной обработке (MPP). Он выполняет следующие задачи.  
  
-   Создает планы параллельных запросов и координирует параллельного выполнения запросов на вычислительных узлах.  
  
-   Хранит и координирует метаданные и данные конфигурации для всех баз данных.  
  
-   Управляет базы данных SQL Server PDW проверки подлинности и авторизации.  
  
-   Отслеживает состояние оборудования и программного обеспечения.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) является частью «рецепт» из PDW. Он выполняет следующие задачи.  
  
-   Передача данных с узлов SQL Server PDW.  
  
-   Процессы операций запросов, требуют передачи данных между узлами.  
  
-   Повышает производительность запросов путем оптимизации скорости передачи данных.  
  
### <a name="admin-console"></a>Административная консоль  
Консоль администратора — веб-приложения, которая представляет состояние устройства, работоспособности и сведения о производительности.  
  
### <a name="configuration-manager"></a>диспетчер конфигураций  
Configuration Manager (dwconfig.exe) — это средство, используйте Администраторы устройств, чтобы настроить Analytics Platform System.  
  
### <a name="control-node-databases"></a>Базы данных узла управления  
SQL Server управляет всеми базами данных на узел элемента управления.  
  
-   База данных оболочки управляет метаданными для всех распределенных пользовательских баз данных.  
  
-   TempDB содержит метаданные для всех временных таблиц пользователя на устройстве.  
  
-   Образец является главной таблицы для SQL Server на узел элемента управления.  
  
### <a name="compute-node"></a>Вычислительный узел  
Вычислительные узлы являются параллельную обработку данных и устройства хранения. Они непосредственно подключенное хранилище и использовать SQL Server для управления данными пользователя.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) выполняется на каждом вычислительном узле, чтобы сделать следующее:  
  
-   В ходе обработки параллельных запросов DMS передачи данных из других узлов компьютера и узел элемента управления.  
  
-   DMS, работающих на каждом вычислительном узле получает загружает данные в параллельном режиме. Загрузить данные в параллельном режиме непосредственно на сервере загрузки для вычислительных узлов  
  
-   DMS передает данные из каждого узла вычислительного непосредственно на сервер резервного копирования.  
  
-   С помощью PolyBase, DMS передает данные из внешних кластера Hadoop или область HDInsight и на устройстве.  
  
### <a name="compute-node-databases"></a>Вычислений узел баз данных 
Каждый вычислительный узел работает экземпляр SQL Server для обработки запросов и управления данными пользователя.  
  
## <a name="appliance-fabric"></a>Структура устройства  
Структура устройства предоставляет операционной системы, службы и сетевой инфраструктуры для устройства.  
  
### <a name="domain-controller"></a>Контроллер домена  
Доменных служб Active Directory (AD) (DS)  
Система платформы аналитики проводит проверку подлинности между узлами Analytics Platform System и управляет проверкой подлинности имен входа для проверки подлинности Windows для SQL Server PDW.  
  
Служба DNS  
Службы доменных имен (DNS) разрешает доменные имена в IP-адреса для устройства Analytics Platform System.  
  
### <a name="windows-deployment-service"></a>Службы развертывания Windows  
Службы развертывания Windows (WDS) выполняет развертывание операционной системы Windows Server на устройстве. Оно развертывается на каждом узле и виртуальных машин на устройстве.  
  
Служба DHCP создает IP-адреса, узлы в пределах области устройства можно присоединиться к сети устройство без необходимости предварительно настроенный IP-адрес.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Система платформы аналитики использует виртуализацию для достижения высокой доступности. Virtual Machine Manager размещает System Center для развертывания операционной системы на физических узлах.  
  
Windows Server Update Services (WSUS) для применения или удаления обновления Windows для всех узлов и виртуальных машин.  
  
### <a name="windows-server"></a>Windows Server  
Выполнить все узлы и виртуальные машины в устройстве операционной системы Windows Server.  
  
### <a name="failover-clustering"></a>Отказоустойчивая кластеризация  
Отказоустойчивая кластеризация Windows предоставляет возможность перезапуска процессов на пассивном узле в случае, если происходит сбой узла.  
  
### <a name="storage-spaces"></a>Дисковые пространства  
Дисковые пространства Windows управляет данными пользователя в качестве пула носителей для небольшой группы вычислительных узлов. При сбое вычислительных узлов, данные по-прежнему доступен через другой вычислительных узлов в группе.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server предоставляет простое и надежное решение виртуализации. Система платформы аналитики использует виртуализации для распределения ресурсов ЦП и обеспечения высокой доступности узлов PDW и устройством компоненты структуры.  
  
## <a name="sec2"></a>Не реляционных данных
Технология PolyBase, интегрируется с внешними данными Hadoop данных SQL Server PDW. Данные Hadoop могут храниться на любом из этих источников данных Hadoop.  
  
-   Hortonworks для Linux или Windows Server  
  
-   Cloudera в Linux  
  
-   HDInsight под управлением APS  
  
-   HDInsight данные, хранящиеся на BLOB-объекта хранилища Azure  
  
## <a name="query-tools"></a>Средства запросов   
  
Запросы пишутся с Transact\-SQL изменено в соответствии с характером MPP запросов. Все запросы отправляются к узлу элемента управления, который создает план параллельных запросов, чтобы выполнить запрос на вычислительных узлах.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools запускается внутри Visual Studio и является нашей рекомендуемые Графический интерфейс для отправки запросов к SQL Server PDW. Это похоже на SQL Server Management Studio, позволяя просматривать обозреватель объектов.  
  
Если у вас еще нет Visual Studio, можно загрузить бесплатно нужные инструменты. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Средство командной строки запроса sqlcmd  
sqlcmd является средством командной строки SQL Server для запуска Transact\-SQL инструкций и команд системы. Он работает с SQL Server PDW и наши рекомендуемое средство командной строки для выполнения запросов к SQL Server PDW. Программа sqlcmd позволяет выполнить Transact\-инструкций SQL в интерактивном режиме из командной строки, как пакетного файла или из Windows PowerShell.  
  
<!-- MISSING LINKS

If you don’t have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Службы Integration Services  
Службы Integration Services можно использовать для запроса SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Linked Server  
С помощью подключения к серверу SQL Server связаны, SQL Server может использоваться для передачи Transact\-инструкции SQL для SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Средства бизнес-аналитики
  
Службы Analysis Services  
SQL Server PDW является допустимый источник данных для баз данных служб Analysis Services и PowerPivot для Excel модели. С помощью поставщика OLE DB, можно настроить куб служб Analysis Services для использования многомерной интерактивной аналитической обработки (MOLAP) или хранилища реляционная интерактивная аналитическая обработка (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>построитель отчетов  
SQL Server PDW можно использовать в качестве источника данных SQL Server для отчетов, разрабатываемых с помощью построителя отчетов SQL Server для служб Reporting Services. SQL Server PDW также можно использовать как источник данных SQL Server для моделей отчетов. С помощью диспетчера отчетов или API сервера отчетов, можно создать модель из базы данных SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot для Excel  
Можно подключиться к SQL Server PDW с PowerPivot для Excel, бесплатной загрузки, который значительно расширяет возможности анализа данных Excel.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Загрузка средств 
  
### <a name="integration-services"></a>Службы Integration Services  
Установка конкретного PDW назначения адаптеров, которые позволяют использовать службы SQL ServerIntegration для загрузки данных в SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader загрузчика командной строки  
dwloader является средством командной строки загрузки, которое загружает данные в параллельном режиме с сервера загрузки с узлами SQL Server PDW вычислений. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase Hadoop интеграции  
Технология PolyBase можно загрузить из кластера Hadoop нереляционных данных в реляционной таблице в SQL Server PDW. Данные Hadoop может располагаться во внешнем кластера Hadoop области HDI на точках доступа, или в BLOB-объекта хранилища Azure.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Резервное копирование базы данных и восстановление  
SQL Server PDW использует Transact\-SQL резервная копия базы данных и восстановить команды резервного копирования и восстановления пользовательских баз данных, в параллельном режиме и с резервного копирования сервера. SQL Server PDW записывает резервные копии в каталог, в общую папку Windows и аналогично восстанавливает данные из общей папки Windows.  
  
Дополнительные сведения см. в разделе [Планирование резервного копирования и загрузки оборудования](backup-and-loading-hardware.md) и [резервное копирование и восстановление: Обзор](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Копирование удаленной таблицы  
Функция удаленной копии таблицы позволяет копировать таблицы из базы данных SQL Server PDW для удаленных баз данных SMP SQL Server (отличных от устройства). Это позволяет использовать сценарии звезда для SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Наблюдение  
Система платформы аналитики имеет несколько способов для отслеживания активности устройства  
  
### <a name="admin-console"></a>Административная консоль  
Консоль администрирования дает возможность просмотра текущего состояния о работоспособности устройства. Это работает как веб-приложения на узел элемента управления и доступен по протоколу https.  
  
Дополнительные сведения см. в разделе [отслеживать устройства с помощью консоли администрирования &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Системные представления  
Консоль администрирования основана на представление системных запросов. Вы можете запрашивать системные представления отдельно, чтобы получить конкретные сведения, которые вам необходимы.  

Дополнительные сведения см. в разделе [отслеживать устройства с помощью системных представлений &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Существуют пакеты управления System Center Operations Manager (SCOM) для SQL Server PDW. 

Чтобы настроить устройство для SCOM, см. [отслеживать устройства с помощью System Center Operations Manager &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
