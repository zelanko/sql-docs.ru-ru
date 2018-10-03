---
title: Запуск пакетов служб Integration Services (SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/04/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.ispackageexecute.f1
- sql13.ssis.ssms.executepackage.f1
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
- executing packages [Integration Services]
- running packages [Integration Services]
- Integration Services, (See also Integration Services packages)
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b46ed84db9ad5339639119a8d5f29644c7be8fc7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757342"
---
# <a name="run-integration-services-ssis-packages"></a>Запуск пакетов служб Integration Services (SSIS)
  Чтобы запустить пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , можно воспользоваться одним из предостовляемых средств. Выбор средства зависит от места хранения пакета. Эти средства приведены в следующей таблице.  

> [!NOTE]
> В этой статье приводятся общие сведения о выполнении пакетов служб SSIS, а также содержится информация о выполнении пакетов в локальной среде. Выполнять пакеты служб SSIS можно на следующих платформах:
> - **облако Microsoft Azure**. Дополнительные сведения см. в статьях [Перенос рабочих нагрузок SQL Server Integration Services в облако](../lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md) и [Выполнение пакета служб SSIS в Azure](../lift-shift/ssis-azure-run-packages.md).
> - **Linux**. Дополнительные сведения см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../../linux/sql-server-linux-migrate-ssis.md).
  
 Чтобы сохранить пакет на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используется модель развертывания проекта. Сведения см. в разделе [Развертывание проектов и пакетов служб Integration Services (SSIS)](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Чтобы сохранить пакет в хранилище пакетов SSIS, базе данных msdb, или в файловой системе, используется модель развертывания пакета. Дополнительные сведения см. в разделе [Устаревшее развертывание пакетов (службы SSIS)](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
|Инструмент|Пакеты, хранимые на сервере служб Integration Services|Пакеты, которые находятся в хранилище пакетов служб SSIS предыдущих версий или в базе данных msdb.|Пакеты, хранимые в файловой системе вне расположения входящего в состав хранилища пакетов SSIS.|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|нет|нет<br /><br /> Однако существующий пакет можно добавить в проект из хранилища пакетов [!INCLUDE[ssIS](../../includes/ssis-md.md)] , включающего в себя базу данных msdb. При добавлении существующего пакета в проект таким методом локальная копия пакета создается в файловой системе.|Да|  
|**В среде SQL Server Management Studio, если установлено соединение с экземпляром ядра СУБД, где размещен сервер служб Integration Services.**<br /><br /> Дополнительные сведения см. в разделе [Execute Package Dialog Box](#execute_package_dialog).|Да|нет<br /><br /> Однако из этих расположений пакет можно импортировать на сервер.|нет<br /><br /> Однако пакет можно импортировать на сервер из файловой системы.|
|**В среде SQL Server Management Studio, если установлено соединение с экземпляром ядра СУБД, где размещен сервер служб Integration Services, заданный в качестве мастера масштабирования.**<br /><br /> Дополнительные сведения см. в статье [Execute packages in Scale Out](../../integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md) (Выполнение пакетов при масштабном развертывании).|Да|нет|нет|
|**В среде SQL Server Management Studio, если установлено соединение со службами Integration Services, управляющими хранилищем пакетов служб SSIS.**|нет|Да|нет<br /><br /> Однако пакет можно импортировать в хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] из файловой системы.|  
|**dtexec**<br /><br /> Дополнительные сведения см. в статье [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|Да|Да|Да|  
|**dtexecui**<br /><br /> Дополнительные сведения см. в разделе [Справочник по пользовательскому интерфейсу программы выполнения пакетов (DtExecUI)](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md).|нет|Да|Да|  
|**Агент SQL Server**<br /><br /> Чтобы запланировать запуск пакета, используйте задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Дополнительные сведения см. в статье [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).|Да|Да|Да|  
|**Встроенная хранимая процедура**<br /><br /> Дополнительные сведения см. в разделе [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).|Да|нет|нет|  
|**Управляемые API, использующие типы и элементы пространства имен** <xref:Microsoft.SqlServer.Management.IntegrationServices>|Да|нет|нет|  
|**Управляемые API, использующие типы и элементы пространства имен** <xref:Microsoft.SqlServer.Dts.Runtime>|В настоящее время нет|Да|Да|  

## <a name="execution-and-logging"></a>Выполнение и ведение журнала  
 Данные о пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут заноситьтся в журнал выполнения, данные времени исполнения могут сохраняться в файлах журнала. Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
 С помощью отчетов о выполнении можно отслеживать пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , развернутые и выполняемые на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Отчеты доступны в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../integration-services/performance/monitor-running-packages-and-other-operations.md#reports).  
  
## <a name="run-a-package-in-sql-server-data-tools"></a>Запуск пакета с помощью SQL Server Data Tools
  Обычно пакеты исполняются в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] во время разработки, отладки и тестирования пакетов. Когда пакет запускается из конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , его запуск происходит немедленно.  
  
 Во время выполнения пакета конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] отображает ход выполнения пакета на вкладке **Выполнение** . Можно видеть время начала и завершения выполнения пакета, его задачи и контейнеры — наряду с данными о задачах или контейнерах пакета, завершившегося ошибкой. По завершении выполнения пакета на вкладке **Результаты выполнения** сохраняются сведения о ходе выполнения. Дополнительные сведения см. в подразделе «Отчет о состоянии» раздела [Debugging Control Flow](../../integration-services/troubleshooting/debugging-control-flow.md).  
  
 **Развертывание времени проектирования**. Когда запуск пакета произведен в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], происходит построение пакета и затем его развертывание в папку. Перед запуском пакета можно указать папку, в которой будет производиться развертывание пакета. Если папка не указана, то по умолчанию используется папка **bin** . Этот тип развертывания называется развертыванием времени разработки.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>Запуск пакета с помощью SQL Server Data Tools  
  
1.  Если решение содержит несколько проектов, щелкните в обозревателе решений правой кнопкой мыши папку проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащую пакет, и задайте стартовый проект, выбрав пункт **Установить в качестве автоматически запускаемого объекта** .  
  
2.  Если проект содержит несколько пакетов, щелкните в обозревателе решений правой кнопкой мыши пакет и задайте стартовый пакет, выбрав пункт **Установить в качестве автоматически запускаемого объекта** .  
  
3.  Чтобы запустить пакет, выполните одну из следующих процедур.  
  
    -   Откройте пакет, который необходимо запустить, затем выберите пункт **Начать отладку** в меню или нажмите клавишу F5. После исполнения пакета нажмите клавиши Shift+F5 для возврата в режим конструктора.  
  
    -   В обозревателе решений щелкните правой кнопкой мыши пакет, после чего выберите пункт **Выполнить пакет**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>Задание каталога для развертывания времени разработки  
  
1.  В обозревателе решений щелкните правой кнопкой мыши папку проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащую запускаемый пакет, затем выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Страницы свойств \<имя проекта>** выберите элемент **Сборка**.  
  
3.  Обновите значения свойства OutputPath для указания папки, которую необходимо использовать для развертывания времени разработки, и нажмите кнопку **ОК**.  


## <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a>Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio
  После развертывания проекта на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакет можно запускать на сервере.  
  
 В отчетах об операциях можно просматривать сведения о выполненных или выполняемых в данный момент на сервере пакетах. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../integration-services/performance/monitor-running-packages-and-other-operations.md#reports).  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a>Запуск пакета на сервере с помощью среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором содержится каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните узел служб **Integration Services Catalogs** , разверните узел **SSISDB** и перейдите к пакету, содержащемуся в развернутом вами проекте.  
  
3.  Щелкните имя пакета правой кнопкой мыши и выберите команду **Выполнить**.  
  
4.  Настройте выполнение пакета с помощью параметров на вкладках **Параметры**, **Диспетчеры соединений**и **Расширенные** диалогового окна **Выполнение пакета** .  
  
5.  Нажмите кнопку **ОК** , чтобы выполнить пакет.  
  
     -или-  
  
     Используйте хранимую процедуру для запуска пакета. Щелкните **Скрипт** , чтобы сформировать инструкцию Transact-SQL, которая создает и запускает экземпляр выполнения. Инструкция включает в себя вызов хранимых процедур catalog.create_execution, catalog.set_execution_parameter_value и catalog.start_execution. Дополнительные сведения об этих хранимых процедурах см. в разделах [catalog.create_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md) и [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).  

## <a name="execute_package_dialog"></a> Execute Package Dialog Box
  Используйте диалоговое окно **Выполнение пакета** , чтобы запустить пакет, хранящийся на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может содержать параметры, значения которых хранятся в переменных среды. Перед выполнением такого пакета необходимо указать, какая среда будет применяться для задания значений переменных среды. Проект может содержать несколько сред, но для привязки значений переменных среды во время выполнения может использоваться только одна среда. Если в пакете не используются переменные среды, среда не требуется.  
  
 Выбор действия  
  
-   [Открытие диалогового окна «Выполнение пакета»](#open_dialog)  
  
-   [Задание параметров на странице «Общие»](#general)  
  
-   [Задание параметров на вкладке «Параметры»](#parameters)  
  
-   [Задание параметров на вкладке «Диспетчеры соединений»](#connection)  
  
-   [Задание параметров на вкладке «Дополнительно»](#advanced)  
  
-   [Создание скриптов параметров в диалоговом окне выполнения пакета](#script)  
  
###  <a name="open_dialog"></a> Открытие диалогового окна «Выполнение пакета»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Разверните папку, содержащую пакет, который необходимо запустить.  
  
5.  Щелкните правой кнопкой мыши пакет и выберите команду **Выполнить**.  
  
###  <a name="general"></a> Задание параметров на странице «Общие»  
 Выберите **Среда** для указания среды, которая будет применена с запуском пакета.  
  
###  <a name="parameters"></a> Задание параметров на вкладке «Параметры»  
 На вкладке **Параметры** измените значения параметров, которые используются при выполнении пакета.  
  
###  <a name="connection"></a> Задание параметров на вкладке «Диспетчеры соединений»  
 На вкладке «Диспетчеры соединений» задайте свойства диспетчеров соединений пакета.  
  
###  <a name="advanced"></a> Задание параметров на вкладке «Дополнительно»  
 На вкладке «Дополнительно» выполняется управление свойствами и другими параметрами пакета.  
  
 **Добавить**, **Изменить**, **Удалить**  
 Используйте эти кнопки для добавления, изменения или удаления свойства.  
  
 **Уровень ведения журнала**  
 Выберите уровень ведения журнала для выполнения пакета. Дополнительные сведения см. в разделе [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md).  
  
 **Дамп при ошибках**  
 Укажите, будет ли при возникновении ошибок создаваться файл дампа во время выполнения пакета. Дополнительные сведения см. в статье [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).  
  
 **32-разрядная среда выполнения**  
 Укажите, что пакет будет выполняться в 32-разрядной системе.  
  
###  <a name="script"></a> Создание скриптов параметров в диалоговом окне выполнения пакета  
 Кроме того, в диалоговом окне **Выполнение пакета** вы можете использовать кнопку **Скрипт** на панели инструментов для записи кода [!INCLUDE[tsql](../../includes/tsql-md.md)] . Созданный скрипт вызывает хранимые процедуры [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) с теми же параметрами, которые были выбраны в диалоговом окне **Выполнение пакета**. Скрипт отображается в новом окне скрипта в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  

## <a name="see-also"></a>См. также:  
 [Программа dtexec](../../integration-services/packages/dtexec-utility.md)   
[Запуск мастера импорта и экспорта SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)
  
  
