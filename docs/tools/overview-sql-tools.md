---
title: "Средства SQL и служебные программы для SQL Server, база данных Azure SQL и хранилище данных SQL | Документы Microsoft"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: eccbe54c561e009858f6192126abc57e3399082c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="tools-and-utilities-for-azure-sql-database-sql-server-and-sql-data-warehouse"></a>Средства и служебные программы для базы данных SQL Azure, SQL Server и хранилище данных SQL

[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]  

![](../includes/media/sql-database-tools.png)В этой статье предоставляет список доступных средств для работы с SQL Server, базы данных SQL Azure, хранилище данных SQL и приложений на основе SQL Server. 

Если вы хотите перейти непосредственно в и начните создавать таблицы, выполнение запросов, по сути разработки и управления базой данных, затем [ **SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) вероятнее всего ваш главный инструмент. Среда SSMS предоставляется бесплатно и выполняется в Windows.

Если вы используете macOS или Linux, попробуйте [кода Visual Studio](https://code.visualstudio.com/) с [ **mssql для Visual Studio Code** ](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) расширения. Эти средства предназначены для разработки с широким набором функциональных возможностей Microsoft SQL Server, базы данных SQL Azure и хранилище данных SQL и также свободны. В разделе [кода Visual Studio используется для создания и выполнения скриптов Transact-SQL для SQL Server](../linux/sql-server-linux-develop-use-vscode.md).


## <a name="sql-tools"></a>Средства SQL 
 
| Инструмент | Description |
|:--|:--|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Используйте SQL Server Management Studio (SSMS) для запроса, проектирования и управления SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. |
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Стать мощная среда разработки Visual Studio для SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. |
| [Код Visual Studio](https://code.visualstudio.com/)| Код Visual Studio работает на macOS, Windows и Linux. После установки Visual Studio Code, установить [mssql расширения](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) для разработки Microsoft SQL Server, базы данных SQL Azure и хранилище данных SQL. |
| [Диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Используйте диспетчер конфигурации SQL Server для настройки служб SQL Server и настройки сетевых подключений.|
| [Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md) | Используйте SQL Server Migration Assistant для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|
| [Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md) | Функция распределенного воспроизведения помогут оценить влияние будущих обновлений SQL Server. Также распределенного воспроизведения можно используйте для оценки влияния оборудования и обновления операционной системы и настройки SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Программа ssbdiagnose сообщает о проблемах в диалогах компонента Service Broker или в конфигурации служб компонента Service Broker. |


## <a name="sql-command-prompt-utilities"></a>Программы командной строки SQL

  Программы командной строки позволяют вносить в скрипт операции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
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
|[Программа sqlcmd](../tools/sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|\<*диск*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
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



