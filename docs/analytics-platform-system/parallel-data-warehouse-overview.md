---
title: Компоненты параллельного хранилища данных
description: В этой статье описывается программное обеспечение устройства и программные компоненты, не относящиеся к устройствам, в системе аналитики платформы.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5e609585e464cb52b996f45c7d8c57aaffcd79fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400935"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Компоненты параллельного хранилища данных — система аналитики платформы
В этой статье описывается программное обеспечение устройства и компоненты программного обеспечения, не относящиеся к устройству, в системе аналитики платформы.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Параллельное программное обеспечение хранилища данных](media/parallel-data-warehouse-software.png "Параллельное программное обеспечение хранилища данных")  
  
## <a name="sec1"></a>Программное обеспечение устройства — обработка запросов и хранилище данных пользователя  
  
### <a name="control-node"></a>управляющий узел  
Подсистема MPP  
Подсистема MPP является нервнойом системы массовой параллельной обработки (MPP). Он выполняет следующие действия:  
  
-   Создает параллельные планы запросов и координирует выполнение параллельных запросов на вычислительных узлах.  
  
-   Хранит и координирует метаданные и данные конфигурации для всех баз данных.  
  
-   Управляет проверкой подлинности SQL Server PDW и авторизацией базы данных.  
  
-   Отслеживает состояние оборудования и программного обеспечения.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) является частью «тайна» в PDW. Он выполняет следующие действия:  
  
-   Передает данные на узлы SQL Server PDW и из них.  
  
-   Обрабатывает операции запросов, требующие передачи данных между узлами.  
  
-   Повышает производительность запросов за счет оптимизации скорости передачи данных.  
  
### <a name="admin-console"></a>Административная консоль  
Консоль администрирования — это веб-приложение, которое представляет сведения о состоянии устройства, работоспособности и производительности.  
  
### <a name="configuration-manager"></a>диспетчер конфигураций  
Configuration Manager (dwconfig. exe) — это средство, которое администраторы устройств используют для настройки системы аналитики.  
  
### <a name="control-node-databases"></a>Управление базами данных узлов  
SQL Server управляет всеми базами данных на управляющем узле.  
  
-   База данных оболочки управляет метаданными для всех распределенных пользовательских баз данных.  
  
-   База данных TempDB содержит метаданные для всех временных таблиц пользователя на устройстве.  
  
-   Master — это главная таблица для SQL Server на управляющем узле.  
  
### <a name="compute-node"></a>Узел вычислений  
Вычислительные узлы — это параллельная обработка данных и единицы хранения. Они имеют непосредственно подключенное хранилище и используют SQL Server для управления данными пользователей.  
  
### <a name="data-movement-service-dms"></a>Служба перемещения данных (DMS)  
Служба перемещения данных (DMS) выполняется на каждом кластерном узле для выполнения следующих задач.  
  
-   В ходе обработки параллельных запросов данные передаются в и из других узлов компьютеров и управляющего узла.  
  
-   DMS, выполняющаяся на каждом из вычислений, получает параллельную загрузку данных. Данные загружаются параллельно непосредственно от сервера загрузки к вычисленным узлам.  
  
-   DMS передает данные с каждого расчетного узла непосредственно на резервный сервер.  
  
-   С помощью Polybase, DMS передает данные в внешний кластер Hadoop или Azure Storage Blob.  
  
### <a name="compute-node-databases"></a>Базы данных вычислений узлов 
Каждый вычислительный узел запускает экземпляр SQL Server для обработки запросов и управления данными пользователей.  
  
## <a name="appliance-fabric"></a>Структура устройства  
Структура устройства предоставляет операционную систему, службы и сетевую инфраструктуру для устройства.  
  
### <a name="domain-controller"></a>Контроллер домена  
Доменные службы Active Directory (AD)  
Система аналитики платформы выполняет проверку подлинности узлов системы аналитики и управляет проверкой подлинности SQL Server PDW имен входа для проверки подлинности Windows.  
  
Служба DNS  
Служба доменных имен Windows (DNS) сопоставляет доменные имена с IP-адресами для системного устройства аналитики.  
  
### <a name="windows-deployment-service"></a>Служба развертывания Windows  
Служба развертывания Windows (WDS) развертывает операционную систему Windows Server на устройстве. Он развертывается на каждом узле и виртуальной машине в пределах устройства.  
  
Служба DHCP создает IP-адреса, чтобы узлы в домене устройства могли присоединиться к сети устройства без предварительно настроенного IP-адреса.  
  
### <a name="virtual-machine-manager"></a>Диспетчер виртуальных машин  
Система аналитики платформы использует виртуализацию для достижения высокого уровня доступности. Virtual Machine Manager размещает System Center для развертывания операционной системы на физических узлах.  
  
Windows Server Update Services (WSUS) для применения или удаления обновлений Windows на всех узлах и виртуальных машинах.  
  
### <a name="windows-server"></a>Windows Server  
Все узлы и виртуальные машины на устройстве работают под управлением операционной системы Windows Server.  
  
### <a name="failover-clustering"></a>Отказоустойчивая кластеризация  
Отказоустойчивая кластеризация Windows предоставляет возможность перезапуска процессов на пассивном узле в случае сбоя узла.  
  
### <a name="storage-spaces"></a>Дисковые пространства  
Дисковые пространства Windows управляют данными пользователей как пулом носителей для небольшой группы вычислительных узлов. При сбое вычислений на узле данные по-прежнему доступны через другой узел вычислений в группе.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server предоставляет простое и надежное решение для виртуализации. Система аналитики платформы использует виртуализацию для балансировки ресурсов ЦП и обеспечения высокой доступности для узлов PDW и компонентов структуры устройств.  
  
## <a name="sec2"></a>Нереляционные данные
Технология Polybase интегрирует SQL Server PDW данные с внешними данными Hadoop. Данные Hadoop могут храниться в любом из следующих источников данных Hadoop:  
  
-   Распространение Hortonworks Hadoop  
  
-   Cloudera распределение Hadoop  
  
-   Данные HDInsight, хранящиеся на Azure Storage Blob  
  
## <a name="query-tools"></a>Средства запросов   
  
Запросы записываются с\-помощью языка Transact SQL, измененного в соответствии с природой запросов MPP. Все запросы отправляются в управляющий узел, который создает параллельный план запроса для выполнения запроса на всех разных узлах вычислений.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools выполняется в Visual Studio и является рекомендуемым средством графического интерфейса пользователя для отправки запросов в SQL Server PDW. Он похож на SQL Server Management Studio, позволяя перемещаться по обозревателю объектов.  
  
Если у вас еще нет Visual Studio, вы можете скачать необходимые средства бесплатно. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Средство запросов командной строки sqlcmd  
sqlcmd — это SQL Server программа командной строки для выполнения инструкций Transact\-SQL и системных команд. Он работает с SQL Server PDW и является рекомендуемым средством командной строки для запроса SQL Server PDW. С помощью программы sqlcmd можно выполнять\-инструкции Transact SQL в интерактивном режиме из командной строки, из пакетного файла или из Windows PowerShell.  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Службы Integration Services  
Integration Services можно использовать для запроса SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Связанный сервер  
С помощью SQL Server соединения с связанным сервером можно использовать SQL Server для отправки инструкций Transact\-SQL в SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Средства бизнес-аналитики
  
### <a name="analysis-services"></a>Службы Analysis Services  
SQL Server PDW является допустимым источником данных для Analysis Services баз данных и моделей Excel PowerPivot. С помощью поставщика OLE DB можно настроить куб Analysis Services для использования многомерной оперативной обработки (MOLAP) или хранилища реляционной оперативной аналитической обработки (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>построитель отчетов  
SQL Server PDW можно использовать в качестве источника данных SQL Server для отчетов, разрабатываемых для Reporting Services с помощью SQL Server построитель отчетов. SQL Server PDW также можно использовать в качестве источника SQL Server для моделей отчетов. С помощью диспетчер отчетов или API сервера отчетов можно создать модель из базы данных SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot для Excel  
Вы можете подключиться к SQL Server PDW с помощью PowerPivot для Excel, бесплатной загрузки, которая значительно расширяет возможности анализа данных в Excel.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Загрузка средств 
  
### <a name="integration-services"></a>Службы Integration Services  
Установите адаптеры назначения для PDW, которые позволяют использовать службы SQL Серверинтегратион для загрузки данных в SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader загрузчик командной строки  
dwloader — это средство загрузки из командной строки, которое загружает данные параллельно с сервера загрузки на SQL Server PDWные на расчетные узлы. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>Polybase для интеграции с Hadoop  
Технология Polybase позволяет загружать нереляционные данные из кластера Hadoop в реляционную таблицу в SQL Server PDW. Данные Hadoop могут находиться во внешнем кластере Hadoop или в Azure Storage Blob.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Резервное копирование и восстановление базы данных  
SQL Server PDW использует команды резервного копирования и восстановления базы данных Transact-SQL для резервного копирования и восстановления пользовательских баз данных в параллельном режиме и обратно на резервный сервер. SQL Server PDW записывает резервную копию в каталог в общей папке Windows, а затем восстанавливает данные из общей папки Windows.  
  
Дополнительные сведения см. в разделе [Планирование резервного копирования и загрузка оборудования](backup-and-loading-hardware.md) и [резервного копирования и восстановления](backup-and-restore-overview.md) .  
  
## <a name="remote-table-copy"></a>Копирование удаленной таблицы  
Функция копирования удаленных таблиц позволяет копировать таблицы из баз данных SQL Server PDW в удаленные (не устройства) SQL Server базы данных SMP. Это позволяет выполнять сценарии с центральным и периферийным SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Наблюдение  
Система аналитики платформы имеет несколько способов мониторинга активности устройства  
  
### <a name="admin-console"></a>Административная консоль  
Консоль администрирования позволяет просматривать текущее состояние работоспособности устройства. Это выполняется как веб-приложение на узле управления и доступно по протоколу HTTPS.  
  
Дополнительные сведения см. [в разделе мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Системные представления  
Консоль администрирования основана на запросах системного представления. Вы можете выполнять запросы к системным представлениям по отдельности, чтобы получить конкретный необходимый фрагмент информации.  

Дополнительные сведения см. [в разделе мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Существует System Center Operations Manager пакетов управления (SCOM) для SQL Server PDW. 

Сведения о настройке устройства для SCOM см. в статье [мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
