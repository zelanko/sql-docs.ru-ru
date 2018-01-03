---
title: "Средства и программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL SQL | Документы Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: "0"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 792d80357f62fcc76576dad24105edead20dac44
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Средства и программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


## <a name="tools-to-run-queries-and-manage-databases"></a>Средства для выполнения запросов и управления базами данных  

| Инструмент | Description |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]— это бесплатная, упрощенная средство для управления базами данных везде, где они выполняются. Эта предварительная версия предоставляет возможности управления базы данных, включая расширенного редактора Transact-SQL и настраиваемые представление о работоспособности баз данных. **[!INCLUDE[name-sos](../includes/name-sos-short.md)]выполняется на Windows, Linux и macOS**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Используйте SQL Server Management Studio (SSMS) для запроса, проектирования и управления SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. **Среда SSMS запущена на Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Стать мощная среда разработки Visual Studio для SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. **Набор SSDT работает в Windows**.|
| [Код Visual Studio](https://code.visualstudio.com/)| После установки Visual Studio Code, установить [mssql расширения](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) для разработки Microsoft SQL Server, базы данных SQL Azure и хранилище данных SQL. **Visual Studio код выполняется на Windows, Linux и macOS**.|

## <a name="which-tool-should-i-choose"></a>Какие средства следует выбрать?

- Вы действительно хотите управлять экземпляр SQL Server или базы данных, в редакторе недоступно в Windows, Linux или Mac? Выберите[[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] 
- Вы действительно хотите управлять экземпляр SQL Server или базы данных в Windows с полной поддержкой графического пользовательского интерфейса? Выберите [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Сделать нужно создавать и изменять код базы данных, включая проверки во время компиляции, рефакторинга и конструктор, поддерживают в Windows? Выберите [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Вы действительно хотите создать сценарии T-SQL в редакторе недоступно в Windows, Linux или Mac? Выберите [кода Visual Studio](https://code.visualstudio.com/) и [mssql расширения](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Дополнительные средства

| Инструмент | Description |
|:--|:--|
| [Диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Используйте диспетчер конфигурации SQL Server для настройки служб SQL Server и настройки сетевых подключений.|
| [Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md) | Используйте SQL Server Migration Assistant для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|
| [Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md) | Функция распределенного воспроизведения помогут оценить влияние будущих обновлений SQL Server. Также распределенного воспроизведения можно используйте для оценки влияния оборудования и обновления операционной системы и настройки SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Программа ssbdiagnose сообщает о проблемах в диалогах компонента Service Broker или в конфигурации служб компонента Service Broker. |


## <a name="command-line-utilities"></a>Программы командной строки

  Служебные программы командной строки позволяют вносить в скрипт [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] операций. В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Служебная программа**|**Описание**|**Установлена в**|  
|-----------------|---------------------|----------------------|  
|[Программа bcp](../tools/bcp-utility.md)|Используется для копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|\<*диск*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta, программа](../tools/dta/dta-utility.md)|Используется для анализа рабочей нагрузки и дает рекомендации по структурам физического проектирования, чтобы оптимизировать производительность сервера с этой рабочей нагрузкой.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа dtexec](../integration-services/packages/dtexec-utility.md)|Используется для настройки и выполнения пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Версия этой программы с пользовательским интерфейсом называется **DTExecUI**. Она вызывает служебную программу для запуска пакетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа dtutil](../integration-services/dtutil-utility.md)|Используется для управления пакетами служб SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Развертывание решений моделей с использованием программы развертывания](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Используется для развертывания проектов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-scripter (Предварительная версия)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Используется для создания сценариев СОЗДАНИЯ и вставки T-SQL для объектов базы данных в SQL Server, базы данных SQL Azure и хранилище данных SQL Azure.|См. наш [в репозитории GitHub](https://github.com/Microsoft/sql-xplat-cli) для загрузки и использования информации.| 
|[Программа osql](../tools/osql-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение SQL Profiler](../tools/profiler-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Служебная программа RS.exe (SSRS)](../reporting-services/tools/rs-exe-utility-ssrs.md)|Используется для запуска скриптов, предназначенных для управления серверами отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rsconfig (SSRS)](../reporting-services/tools/rsconfig-utility-ssrs.md)|Используется для настройки соединения сервера отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rskeymgmt (SSRS)](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Используется для управления ключами шифрования на сервере отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlagent90](../tools/sqlagent90-application.md)|Используется для запуска агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки.|\<диск >: \Program Files\Microsoft SQL Server\\<*имя_экземпляра*> \MSSQL\Binn|  
|[Служебная программа sqlcmd](../tools/sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|\<*диск*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Программа SQLdiag](../tools/sqldiag-utility.md)|Используется для сбора диагностических сведений для службы поддержки пользователей [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqllogship](../tools/sqllogship-application.md)|Используется приложениями для выполнения операций резервирования, копирования и восстановления, а также связанных с ними задач очистки в конфигурации доставки журналов без запуска соответствующих заданий.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа SqlLocalDB](../tools/sqllocaldb-utility.md)|Режим выполнения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , рассчитанный на разработчиков программ.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Программа sqlmaint](../tools/sqlmaint-utility.md)|Служит для выполнения планов обслуживания баз данных, созданных в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<диск >: \Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Программа sqlps](../tools/sqlps-utility.md)|Используется для выполнения команд и скриптов PowerShell. Загружает и регистрирует командлеты и поставщика PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlservr](../tools/sqlservr-application.md)|Служит для запуска и остановки экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] из командной строки при устранении неполадок.|\<диск >: \Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Программа SSMS](../tools/sql-server-management-studio/ssms-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Программа tablediff](../tools/tablediff-utility.md)|Используется для сравнения данных в двух таблицах, чтобы обнаружить отсутствие конвергенции. Это полезно для устранения неполадок в топологии репликации.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Соглашения о синтаксисе программ командной строки SQL  
  
|**Обозначение**|**Используется для**|  
|--------------------|------------------|  
|ВЕРХНИЙ РЕГИСТР|Инструкции и термины, используемые на уровне операционной системы.|  
|`monospace`|Образцы команд и программного кода.|  
|*курсив*|Параметры, указываемые пользователем.|  
|**полужирный**|Команды, параметры и другие элементы синтаксиса, которые должны в точности соответствовать примеру.|  


