---
title: SQL средства и служебные программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL | Документация Майкрософт
ms.custom: ''
ms.date: 02/22/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: misc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8f31d6479a0a2ba5e5f19f6a0739ab6322de92b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458988"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>Средства и программы для SQL Server, база данных Azure SQL и хранилище данных Azure SQL SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Для управления (запросов, монитор, и т.д.) требуется инструмент базы данных. Существует несколько инструменты для баз данных. Хотя базы данных могут работать в облаке, на Windows или на [Linux](../linux/sql-server-linux-overview.md), ваше средство не должен выполняться на той же платформе, что и база данных. 

В этой статье сведения о доступных средства для работы с базами данных SQL. 


## <a name="tools-to-run-queries-and-manage-databases"></a>Средства для выполнения запросов и управления базами данных  

| Инструмент | Описание |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] — это бесплатные, облегченные средство для управления базами данных везде, где они выполняются. Эта предварительная версия предоставляет возможности управления базы данных, включая расширенного редактора Transact-SQL и настраиваемые ценные сведения о работоспособности баз данных. **[!INCLUDE[name-sos](../includes/name-sos-short.md)] работает в Windows, macOS и Linux**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Используйте SQL Server Management Studio (SSMS) для запроса, проектирования и управления SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. **Среда SSMS запущена на Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Visual Studio можно Превратите в мощную среду разработки для SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. **Набор SSDT работает на Windows**.|
|[MSSQL-cli](mssql-cli.md)|MSSQL-cli является это интерактивное средство командной строки для выполнения запросов к SQL Server. **MSSQL-cli работает в Windows, macOS и Linux**|
| [Visual Studio Code](https://code.visualstudio.com/);| После установки Visual Studio Code, установить [расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) по разработке Microsoft SQL Server, базы данных SQL Azure и хранилище данных SQL. **Запускает Visual Studio Code в Windows, macOS и Linux**.|

## <a name="which-tool-should-i-choose"></a>Какое средство следует выбрать?

- Вы хотите управлять на экземпляре SQL Server или базу данных, в редакторе недоступно: в Windows, Linux или Mac? Выберите [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- Вы хотите управлять на экземпляре SQL Server или базу данных в Windows с полной поддержкой графического пользовательского интерфейса? Выберите [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- Сделать нужно создать или настроить код базы данных, включая проверки во время компиляции, рефакторинга и конструктор, поддерживают на Windows? Выберите [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Вы действительно хотите запросить SQL Server с помощью функции IntelliSense, синтаксис высокого освещения, средство командной строки и многое другое? Выберите [mssql-cli](mssql-cli.md)
- Вы хотите написать сценарии T-SQL в редакторе недоступно: в Windows, Linux или Mac? Выберите [Visual Studio Code](https://code.visualstudio.com/) и [расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Дополнительные средства

| Инструмент | Описание |
|:--|:--|
| [Диспетчер конфигураций](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Используйте диспетчер конфигурации SQL Server для настройки служб SQL Server и настройках сетевого взаимодействия. Configuration Manager работает на Windows|
|[MSSQL-conf](../linux/sql-server-linux-configure-mssql-conf.md)|Используйте mssql-conf, чтобы настроить SQL Server на Linux.|
| [Помощник по миграции SQL Server](../ssma/sql-server-migration-assistant.md) | Помощник по миграции SQL Server используется для автоматизации миграции баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и Sybase.|
| [Распределенное воспроизведение](../tools/distributed-replay/install-distributed-replay-overview.md) | Используйте компонента распределенного воспроизведения, которые помогут оценить влияние будущих обновлений SQL Server. Также можно используйте распределенного воспроизведения для оценки влияния оборудования и обновления операционной системы и настройке SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Программа ssbdiagnose сообщает о проблемах в диалогах компонента Service Broker или в конфигурации служб компонента Service Broker. |


## <a name="command-line-utilities"></a>Программы командной строки

  Программы командной строки позволяют вносить в сценарий операции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Служебная программа**|**Описание**|**Установлена в**|  
|-----------------|---------------------|----------------------|  
|[Программа bcp](../tools/bcp-utility.md)|Используется для копирования данных между экземпляром [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|\<*диск*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta, программа](../tools/dta/dta-utility.md)|Используется для анализа рабочей нагрузки и дает рекомендации по структурам физического проектирования, чтобы оптимизировать производительность сервера с этой рабочей нагрузкой.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа dtexec](../integration-services/packages/dtexec-utility.md)|Используется для настройки и выполнения пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Версия этой программы с пользовательским интерфейсом называется **DTExecUI**. Она вызывает служебную программу для запуска пакетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа dtutil](../integration-services/dtutil-utility.md)|Используется для управления пакетами служб SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Развертывание решений моделей с использованием программы развертывания](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Используется для развертывания проектов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-scripter (Предварительная версия)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Используется для создания сценариев CREATE и INSERT T-SQL для объектов базы данных в SQL Server, базы данных SQL Azure и хранилище данных SQL Azure.|См. в разделе наших [репозиторий GitHub](https://github.com/Microsoft/sql-xplat-cli) для загрузки и сведения об использовании.| 
|[Программа osql](../tools/osql-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение SQL Profiler](../tools/profiler-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Служебная программа RS.exe (SSRS)](../reporting-services/tools/rs-exe-utility-ssrs.md)|Используется для запуска скриптов, предназначенных для управления серверами отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rsconfig (SSRS)](../reporting-services/tools/rsconfig-utility-ssrs.md)|Используется для настройки соединения сервера отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа rskeymgmt (SSRS)](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Используется для управления ключами шифрования на сервере отчетов.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlagent90](../tools/sqlagent90-application.md)|Используется для запуска агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки.|\<диск>:\Program Files\Microsoft SQL Server\\<*имя_экземпляра*>\MSSQL\Binn|  
|[Служебная программа sqlcmd](../tools/sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|\<*диск*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Программа SQLdiag](../tools/sqldiag-utility.md)|Используется для сбора диагностических сведений для службы поддержки пользователей [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqllogship](../tools/sqllogship-application.md)|Используется приложениями для выполнения операций резервирования, копирования и восстановления, а также связанных с ними задач очистки в конфигурации доставки журналов без запуска соответствующих заданий.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа SqlLocalDB](../tools/sqllocaldb-utility.md)|Режим выполнения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , рассчитанный на разработчиков программ.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Программа sqlmaint](../tools/sqlmaint-utility.md)|Служит для выполнения планов обслуживания баз данных, созданных в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<диск>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Программа sqlps](../tools/sqlps-utility.md)|Используется для выполнения команд и скриптов PowerShell. Загружает и регистрирует командлеты и поставщика PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlservr](../tools/sqlservr-application.md)|Служит для запуска и остановки экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] из командной строки при устранении неполадок.|\<диск>:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Программа SSMS](../tools/sql-server-management-studio/ssms-utility.md)|Используется для запуска приложения среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Программа tablediff](../tools/tablediff-utility.md)|Используется для сравнения данных в двух таблицах, чтобы обнаружить отсутствие конвергенции. Это полезно для устранения неполадок в топологии репликации.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Соглашения о синтаксисе программ командной строки SQL  
  
|**Обозначение**|**Используется для**|  
|--------------------|------------------|  
|ВЕРХНИЙ РЕГИСТР|Инструкции и термины, используемые на уровне операционной системы.|  
|`monospace`|Образцы команд и программного кода.|  
|*курсив*|Параметры, указываемые пользователем.|  
|**полужирный**|Команды, параметры и другие элементы синтаксиса, которые должны в точности соответствовать примеру.|  



