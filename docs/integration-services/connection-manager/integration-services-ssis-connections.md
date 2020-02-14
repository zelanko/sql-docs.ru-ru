---
title: Соединения служб Integration Services (SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.asvs.connectionmanager.f1
- sql13.dts.designer.adddtsconnection.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- sources [Integration Services], connections
- packages [Integration Services], connections
- destinations [Integration Services], connections
- tasks [Integration Services], connections
- connections [Integration Services], about connections
- connections [Integration Services]
- SQL Server Integration Services packages, connections
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ed4c8c8feacdd41d2e806a4d2d663f639633e07
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71294432"
---
# <a name="integration-services-ssis-connections"></a>Соединения в службах Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Пакеты [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют соединения для выполнения различных задач и реализации функций служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Подключение к источникам и назначениям данных, например текстовым документам, XML-документам, книгам Excel и реляционным базам данных, для извлечения и загрузки данных.  
  
-   Подключение к реляционным базам данных, содержащим ссылочные данные, для выполнения точных или нечетких уточняющих запросов.  
  
-   Подключение к реляционным базам данных для выполнения инструкций SQL, таких как SELECT, DELETE и INSERT, а также хранимых процедур.  
  
-   Соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения задач обслуживания и передачи, таких как резервное копирование баз данных и передача имен входа.  
  
-   Запись строк журнала в текстовые файлы, XML-файлы, таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и конфигурации пакетов в таблицах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для создания временных рабочих таблиц, необходимых для некоторых преобразований.  
  
-   Подключение к проектам и базам данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для доступа к моделям интеллектуального анализа данных, обработке кубов и измерений и запуска DDL-кода.  
  
-   Указание существующих и создание новых файлов и папок для использования их с перечислителями и задачами контейнера «цикл по каждому элементу».  
  
-   Подключение к очередям сообщений и к инструментарию управления Windows (WMI), управляющим объектам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO), сети Интернет и почтовым серверам.  
  
 Чтобы установить эти соединения, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют диспетчеры соединений, как описано в следующем разделе.  
  
## <a name="connection-managers"></a>Диспетчеры соединений  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют диспетчер соединений в качестве логического представления соединения. На стадии разработки устанавливаются свойства диспетчера соединений, которые описывают физическое соединение, создаваемое сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] при выполнении пакета. Например, диспетчер соединений имеет свойство **ConnectionString** , устанавливаемое на стадии разработки. На стадии выполнения значение этого свойства используется для создания физического соединения.  
  
 Пакет может содержать несколько экземпляров диспетчера соединений одного типа, и для каждого из них свойства устанавливаются отдельно. На стадии выполнения каждый экземпляр диспетчера соединений создает соединение со своими атрибутами.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляет несколько типов диспетчеров соединений, которые позволяют пакету подключаться к различным источникам данных и серверам.  
  
-   Встроенные диспетчеры соединений, которые устанавливаются со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Диспетчеры соединений, которые можно загрузить на веб-сайте корпорации [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Можно создать собственный диспетчер соединений, если существующие диспетчеры не отвечают требованиям.  

### <a name="package-level-and-project-level-connection-managers"></a>Диспетчеры подключений на уровне пакета и уровне проекта
Можно создать диспетчер соединений на уровне пакета или на уровне проекта. Диспетчер соединений, созданный на уровне проекта, доступен всем пакетам в проекте. Диспетчер соединений, созданный на уровне пакета, доступен только этому определенному пакету.  
  
 Диспетчеры соединений, созданные на уровне проекта, заменяют источники данных. Это делается для совместного использования соединений к источникам. Чтобы добавить диспетчер соединений на уровне проекта, проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] должен использовать модель развертывания проекта. Когда проект настроен для использования данной модели, в **обозревателе решений** появляется папка **Диспетчеры соединений**, а папка **Источники данных** удаляется из **обозревателя решений**.  
  
> [!NOTE]  
>  Если в пакете нужно использовать источники данных, проект необходимо преобразовать в модель развертывания пакета.  
>   
>  Дополнительные сведения об этих двух моделях и о преобразовании проекта в модель развертывания проектов см. в разделе [Развертывание проектов и пакетов служб Integration Services (SSIS)](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md).

### <a name="built-in-connection-managers"></a>Встроенные диспетчеры соединений  
 В следующей таблице перечислены типы диспетчеров соединений, предоставляемые службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Тип|Описание|Раздел|  
|----------|-----------------|-----------|  
|ADO|Подключается к объектам данных ActiveX (ADO).|[Диспетчер подключений объектов данных ActiveX](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|Подключается к источнику данных при помощи поставщика .NET.|[Диспетчер подключений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|CACHE|Считывает данные из потока данных или из файла кэша (CAW) и может сохранять данные в файле кэша.|[Диспетчер соединений с кэшем](../../integration-services/connection-manager/cache-connection-manager.md)|  
|DQS|Подключается к серверу служб качества данных и базе данных служб Data Quality Services на сервере.|[Диспетчер соединений «Очистка DQS»](../../integration-services/connection-manager/dqs-cleansing-connection-manager.md)|  
|EXCEL|Подключается к файлу книги Excel.|[Диспетчер подключений Excel](../../integration-services/connection-manager/excel-connection-manager.md)|  
|FILE|Подключается к файлу или папке.|[Диспетчер подключений файлов](../../integration-services/connection-manager/file-connection-manager.md)|  
|FLATFILE|Подключается к данным в отдельном неструктурированном файле.|[Диспетчер подключений неструктурированных файлов](../../integration-services/connection-manager/flat-file-connection-manager.md)|  
|FTP|Подключается к FTP-серверу.|[Диспетчер FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager.md)|  
|HTTP|Подключается к веб-серверу.|[Диспетчер HTTP-соединений](../../integration-services/connection-manager/http-connection-manager.md)|  
|MSMQ|Подключается к очереди сообщений.|[Диспетчер подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|  
|MSOLAP100|Подключается к экземпляру служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[Диспетчер подключений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|  
|MULTIFILE|Подключается к нескольким файлам и папкам.|[Диспетчер подключений нескольких файлов](../../integration-services/connection-manager/multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Подключается к нескольким файлам данных и папкам.|[Диспетчер подключений нескольких неструктурированных файлов](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|  
|OLEDB|Подключается к источнику данных при помощи поставщика OLE DB.|[Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|Подключается к источнику данных через ODBC.|[Диспетчер подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|SMOServer|Подключается к серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).|[Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)|  
|SMTP|Подключается к почтовому серверу SMTP.|[Диспетчер SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager.md)|  
|SQLMOBILE|Подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Диспетчер подключений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
|WMI|Подключается к серверу и определяет на нем область инструментария управления Windows (WMI).|[Диспетчер WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager.md)|  
  
### <a name="connection-managers-available-for-download"></a>Диспетчеры соединений, доступные для загрузки  
 В следующей таблице перечислены дополнительные типы диспетчеров соединений, которые вы можете загрузить с веб-сайта [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Перечисленные в следующей таблице диспетчеры соединений работают только с выпусками [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] и [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Тип|Описание|Раздел|  
|----------|-----------------|-----------|  
|ORACLE|Подключается к серверу Oracle \<версия\>.|Диспетчер соединений Oracle — это компонент диспетчера соединений соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
|SAPBI|Подключается к системе SAP NetWeaver BI версии 7.|Диспетчер соединений SAP BI — это компонент диспетчера соединений соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Кроме того, в состав соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft SQL Server 2008 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=262016)(на английском языке).|  
|TERADATA|Подключается к серверу Teradata \<версия\>.|Диспетчер соединений Teradata — это компонент диспетчера соединений соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
  
### <a name="custom-connection-managers"></a>Пользовательские диспетчеры соединений  
 Кроме того, можно создавать пользовательские диспетчеры соединений. Дополнительные сведения см. в разделе [Developing a Custom Connection Manager](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## <a name="create-connection-managers"></a>Создание диспетчеров подключений
  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают набор диспетчеров соединений для соответствия нуждам задач, подключающихся к разным серверам и источникам данных. Диспетчеры соединений используются компонентами потока данных, которые извлекают и загружают данные в разные типы хранилищ данных, и поставщиками журналов, которые записывают журналы на сервер, в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в файл. Например, пакет с задачей «Отправка почты» использует тип диспетчера соединений SMTP, чтобы подключиться к SMTP-серверу. Пакет с заданием «Выполнение SQL» может использовать диспетчер соединений OLE DB, чтобы подключиться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 Для автоматического создания и настройки диспетчеров подключений при создании пакета можно использовать мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Он также поможет вам создать и настроить источники и назначения для диспетчеров подключений. Дополнительные сведения см. в разделе [Create Packages in SQL Server Data Tools](../../integration-services/create-packages-in-sql-server-data-tools.md).  
  
 Вручную создать новый диспетчер соединений и добавить его в существующий пакет можно в области **Диспетчеры соединений** на вкладках **Поток управления**, **Поток данных**и **Обработчики события** конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . В области **Диспетчер соединений** следует выбрать тип создаваемого диспетчера соединений и установить свойства этого диспетчера с помощью диалогового окна, доступного в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Дополнительные сведения см. в подразделе «Использование области "Диспетчеры соединений"» далее в этом разделе.  
  
 После того как диспетчер соединений добавлен к пакету, его можно использовать в задачах, контейнерах «цикл по каждому элементу», источниках, преобразованиях и целевых объектах. Дополнительные сведения см. в разделах [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md), [Контейнер "цикл по каждому элементу"](../../integration-services/control-flow/foreach-loop-container.md) и [Поток данных](../../integration-services/data-flow/data-flow.md).  
  
### <a name="using-the-connection-managers-area"></a>Использование области «Диспетчеры соединений»  
 Диспетчеры соединений можно создавать на вкладках **Поток управления**, **Поток данных**или **Обработчики событий** конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Следующая диаграмма показывает область **Диспетчеры соединений** на вкладке **Поток управления** конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 ![Снимок экрана: конструктор потока управления с пакетом](../../integration-services/connection-manager/media/samplecontrolflow.gif "Снимок экрана: конструктор потока управления с пакетом")    
  
### <a name="32-bit-and-64-bit-providers-for-connection-managers"></a>32-разрядная и 64-разрядная версии поставщиков для диспетчеров соединений  
 Для многих поставщиков, используемых диспетчерами соединений, доступны 32-разрядная и 64-разрядная версии. Среда разработки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — это 32-разрядная среда, поэтому в ней содержатся только 32-разрядные поставщики. Поэтому необходимо настроить диспетчер соединений для использования специального 64-разрядного поставщика, если 32-разрядная версия того же поставщика уже установлена.  
  
 Во время выполнения используется подходящая версия поставщика, даже если во время разработки указана 32-разрядная версия. 64-разрядная версия поставщика может быть запущена, даже если пакет запущен в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
  У обеих версий поставщика один идентификатор. Чтобы предписать использование средой выполнения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] доступной 64-разрядной версии поставщика, установите свойство Run64BitRuntime проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если свойство Run64BitRuntime имеет значение **true**, среда выполнения находит и использует 64-разрядный поставщик; если свойство Run64BitRuntime имеет значение **false**, среда выполнения использует 32-разрядный поставщик. Дополнительные сведения о свойствах, которые можно настраивать в проектах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [Службы Integration Services (SSIS) и среды Studio](https://msdn.microsoft.com/library/ms140028.aspx).   

## <a name="add-a-connection-manager"></a>Добавление диспетчера подключений
###  <a name="wizard"></a> Добавление диспетчера подключений при создании пакета  
  
-   Использование мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
     Помимо создания и настройки диспетчера соединений, этот мастер также поможет создать и настроить источники и назначения, используемые диспетчером соединений. Дополнительные сведения см. в разделе [Create Packages in SQL Server Data Tools](../../integration-services/create-packages-in-sql-server-data-tools.md).  
  
###  <a name="package"></a> Добавление диспетчера подключений в существующий пакет  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  Щелкните правой кнопкой мыши в любом месте области **Диспетчеры подключений** и выполните одной из следующих действий:  
  
    -   Щелкните тип диспетчера соединений для добавления его в пакет.  
  
         -или-  
  
    -   Если тип, который нужно добавить, не перечислен, щелкните **Создать соединение** , чтобы открыть окно **Добавление диспетчера соединений служб SSIS** , выберите тип диспетчера соединений и нажмите кнопку **ОК**.  
  
     Откроется пользовательское диалоговое окно для выбранного типа диспетчера соединений. Дополнительные сведения о типах диспетчеров соединений и доступных параметрах представлены в таблице ниже.  
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер подключений объектов данных ActiveX](../../integration-services/connection-manager/ado-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер подключений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|[Настройка диспетчера подключений ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)|  
    |[Диспетчер подключений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений служб Analysis Services"](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений Excel](../../integration-services/connection-manager/excel-connection-manager.md)|[Редактор диспетчера подключений Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md)|  
    |[Диспетчер подключений файлов](../../integration-services/connection-manager/file-connection-manager.md)|[Редактор диспетчера подключений файлов](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
    |[Диспетчер подключений нескольких файлов](../../integration-services/connection-manager/multiple-files-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений файлов"](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений неструктурированных файлов](../../integration-services/connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Столбцы")](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)|  
    |[Диспетчер подключений нескольких неструктурированных файлов](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Столбцы")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Дополнительно")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Диспетчер FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager.md)|[Редактор диспетчера FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager-editor.md)|  
    |[Диспетчер HTTP-соединений](../../integration-services/connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)|  
    |[Диспетчер подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|[Редактор диспетчера подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md)|  
    |[Диспетчер подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)|  
    |[Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)|[Редактор диспетчера подключений SMO](../../integration-services/connection-manager/smo-connection-manager-editor.md)|  
    |[Диспетчер SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager.md)|[Редактор диспетчера SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager-editor.md)|  
    |[Диспетчер подключений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|[Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager.md)|[Редактор диспетчера WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager-editor.md)|  
  
     Область **Диспетчеры соединений** отображает добавленные диспетчеры соединений.  
  
5.  При необходимости можно щелкнуть правой кнопкой мыши диспетчер соединений, выбрать пункт **Переименовать**и изменить имя диспетчера соединений по умолчанию.  
  
6.  Чтобы сохранить обновленный пакет, щелкните **Сохранить выбранные элементы** в меню **Файл** .  
  
###  <a name="project"></a> Добавление диспетчера подключений на уровне проекта  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В **Обозревателе решений**щелкните правой кнопкой мыши элемент **Диспетчеры соединений**и выберите команду **Новый диспетчер соединений**.  
  
3.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите тип диспетчера соединений и нажмите кнопку **Добавить**.  
  
     Откроется пользовательское диалоговое окно для выбранного типа диспетчера соединений. Дополнительные сведения о типах диспетчеров соединений и доступных параметрах представлены в таблице ниже.  
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер подключений объектов данных ActiveX](../../integration-services/connection-manager/ado-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер подключений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|[Настройка диспетчера подключений ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)|  
    |[Диспетчер подключений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений служб Analysis Services"](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений Excel](../../integration-services/connection-manager/excel-connection-manager.md)|[Редактор диспетчера подключений Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md)|  
    |[Диспетчер подключений файлов](../../integration-services/connection-manager/file-connection-manager.md)|[Редактор диспетчера подключений файлов](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
    |[Диспетчер подключений нескольких файлов](../../integration-services/connection-manager/multiple-files-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений файлов"](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений неструктурированных файлов](../../integration-services/connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Столбцы")](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)|  
    |[Диспетчер подключений нескольких неструктурированных файлов](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Столбцы")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Дополнительно")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Диспетчер FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager.md)|[Редактор диспетчера FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager-editor.md)|  
    |[Диспетчер HTTP-соединений](../../integration-services/connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)|  
    |[Диспетчер подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|[Редактор диспетчера подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md)|  
    |[Диспетчер подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)|  
    |[Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)|[Редактор диспетчера подключений SMO](../../integration-services/connection-manager/smo-connection-manager-editor.md)|  
    |[Диспетчер SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager.md)|[Редактор диспетчера SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager-editor.md)|  
    |[Диспетчер подключений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|[Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager.md)|[Редактор диспетчера WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager-editor.md)|  
  
     Добавленный диспетчер соединений появится в узле **Диспетчеры соединений** в **обозревателе решений**. Также он появится на вкладке **Диспетчеры соединений** в окне **Конструктор служб SSIS** для всех пакетов в проекте. Имя диспетчера соединений на этой вкладке будет иметь префикс **(проект)** для того, чтобы можно было отличить данный диспетчер соединений на уровне проекта от диспетчеров соединений на уровне пакета.  
  
4.  По желанию щелкните правой кнопкой мыши диспетчер соединений в окне **Обозреватель решений** в узле **Диспетчеры соединений** или на вкладке **Диспетчеры соединений** в окне **Конструктор служб SSIS** , нажмите кнопку **Переименовать**и измените имя диспетчера соединений, установленное по умолчанию.  
  
    > [!NOTE]  
    >  На вкладке **Диспетчеры соединений** в окне **Конструктор служб SSIS** нет возможности перезаписать префикс **(проект)** с имени диспетчера соединений. Это сделано намеренно.  

### <a name="add-ssis-connection-manager-dialog-box"></a>Диалоговое окно "Добавление диспетчера соединений со службами SSIS"
Диалоговое окно **Добавление диспетчера соединений служб SSIS** используется для выбора типа соединения, добавляемого в пакет.  
  
 Дополнительные сведения о диспетчерах соединений см. в разделе [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
#### <a name="options"></a>Параметры  
 **Тип диспетчера подключений**  
 Выберите тип соединения, а затем нажмите кнопку **Добавить**, либо дважды щелкните тип соединения, чтобы задать свойства соединения с помощью редактора для каждого из типов соединений.  
  
 **Добавление**  
 Укажите свойства соединения с помощью редактора для каждого из типов соединений.  
   
##  <a name="parameter"></a> Создание параметра для свойства диспетчера подключений  
  
1.  В области **Диспетчеры соединений** щелкните правой кнопкой мыши диспетчер соединений, для которого необходимо создать параметр, и щелкните **Параметризировать**.  
  
2.  Настройка установок параметра в диалоговом окне **Параметризация** . Дополнительные сведения см. в разделе [Parameterize Dialog Box](https://msdn.microsoft.com/library/fac02b6d-d247-447a-8940-e8700c7ac350).  

## <a name="delete-a-connection-manager"></a>Удаление диспетчера подключений 
###  <a name="DeletePackageLevel"></a> Удаление диспетчера подключений из пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  Щелкните правой кнопкой мыши диспетчер соединений, который необходимо удалить, и нажмите кнопку **Удалить**.  
  
     При удалении диспетчера соединений, связанного с элементом (например, с задачей «Выполнение SQL» или источником OLE DB), результат будет следующим.  
  
    -   На элементе пакета, использующем удаленный диспетчер соединений, отображается значок ошибки.  
  
    -   Пакет не проходит проверку.  
  
    -   Выполнение пакета невозможно.  
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
###  <a name="DeleteProjectLevel"></a> Удаление общего диспетчера подключений (диспетчер подключений на уровне проекта)  
  
1.  Для удаления диспетчера соединений на уровне проекта щелкните правой кнопкой мыши диспетчер соединений в узле **Диспетчеры соединений** в окне **Обозреватель решений** и нажмите кнопку **Удалить**. [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] отображает следующее предупреждающее сообщение:  
  
    > [!WARNING]  
    >  При удалении диспетчера соединений на уровне проекта, пакеты, использующие этот диспетчер соединений, могут не запуститься. Это действие нельзя отменить. Продолжить удаление диспетчера соединений?  
  
2.  Нажмите кнопку «ОК», чтобы удалить диспетчер соединений, или кнопку «Отмена», чтобы оставить диспетчер в проекте.  
  
    > [!NOTE]  
    >  Также можно удалить диспетчер соединений на уровне проекта на вкладке **Диспетчер соединений** в окне **Конструктор служб SSIS** , открытом для любого пакета в проекте. Удалить диспетчер можно, щелкнув правой кнопкой мыши диспетчер соединений на вкладке и выбрав **Удалить**. 
    
## <a name="set-the-properties-of-a-connection-manager"></a>Задание свойств диспетчера соединений
Все диспетчеры соединений могут быть настроены в окне **Свойства** .  
  
 Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предлагают пользовательские диалоговые окна для изменения различных типов диспетчеров подключений в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Диалоговое окно имеет различные наборы настроек в зависимости от типа диспетчера соединений.  
  
### <a name="modify-a-connection-manager-using-the-properties-window"></a>Изменение диспетчера подключений в окне "Свойства"  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  В конструкторе служб SSIS перейдите на вкладку **Поток управления** , **Поток данных** или **Обработчик событий** , чтобы получить доступ к области **Диспетчеры соединений** .  
  
4.  Правой кнопкой мыши щелкните диспетчер подключений и выберите пункт **Свойства**.  
  
5.  В окне **Свойства** измените значения свойств. Окно **Свойства** предоставляет доступ к некоторым свойствам, которые не настраиваются через обычный редактор диспетчера соединений.  
  
6.  Нажмите кнопку **ОК**.  
  
7.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
### <a name="modify-a-connection-manager-using-a-connection-manager-dialog-box"></a>Изменение диспетчера подключений в диалоговом окне диспетчера подключений  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Чтобы сделать доступной область [!INCLUDE[ssIS](../../includes/ssis-md.md)] Диспетчеры соединений **, выберите в конструкторе служб** вкладку **Поток управления** , **Поток данных** или **Обработчик события** .  
  
4.  В области **Диспетчеры соединений** дважды щелкните нужный диспетчер подключений для открытия диалогового окна **Диспетчер соединений** . Дополнительные сведения о конкретных типах диспетчеров соединений и настройках каждого из них см. в следующей таблице.  
  
    |Диспетчер соединений|Параметры|  
    |------------------------|-------------|  
    |[Диспетчер подключений объектов данных ActiveX](../../integration-services/connection-manager/ado-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер подключений ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|[Настройка диспетчера подключений ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)|  
    |[Диспетчер подключений служб Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений служб Analysis Services"](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений Excel](../../integration-services/connection-manager/excel-connection-manager.md)|[Редактор диспетчера подключений Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md)|  
    |[Диспетчер подключений файлов](../../integration-services/connection-manager/file-connection-manager.md)|[Редактор диспетчера подключений файлов](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
    |[Диспетчер подключений нескольких файлов](../../integration-services/connection-manager/multiple-files-connection-manager.md)|[Справочник по пользовательскому интерфейсу: диалоговое окно "Добавление диспетчера подключений файлов"](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Диспетчер подключений неструктурированных файлов](../../integration-services/connection-manager/flat-file-connection-manager.md)|[Редактор диспетчера соединений с неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Столбцы")](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений к неструктурированным файлам (страница "Дополнительно")](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md)|  
    |[Диспетчер подключений нескольких неструктурированных файлов](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|[Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Общие")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Столбцы")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Дополнительно")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Редактор диспетчера подключений с несколькими неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[Диспетчер FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager.md)|[Редактор диспетчера FTP-подключений](../../integration-services/connection-manager/ftp-connection-manager-editor.md)|  
    |[Диспетчер HTTP-соединений](../../integration-services/connection-manager/http-connection-manager.md)|[Редактор диспетчера HTTP-сеансов (страница "Сервер")](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)<br /><br /> [Редактор диспетчера HTTP-сеансов (страница "Прокси-сервер")](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)|  
    |[Диспетчер подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md)|[Редактор диспетчера подключений MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md)|  
    |[Диспетчер подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|[Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)|  
    |[Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|[Настройка диспетчера подключений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)|  
    |[Диспетчер соединений SMO](../../integration-services/connection-manager/smo-connection-manager.md)|[Редактор диспетчера подключений SMO](../../integration-services/connection-manager/smo-connection-manager-editor.md)|  
    |[Диспетчер SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager.md)|[Редактор диспетчера SMTP-подключений](../../integration-services/connection-manager/smtp-connection-manager-editor.md)|  
    |[Диспетчер подключений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|[Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Редактор диспетчера подключений SQL Server Compact Edition (страница "Все")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[Диспетчер WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager.md)|[Редактор диспетчера WMI-подключений](../../integration-services/connection-manager/wmi-connection-manager-editor.md)|  
  
5.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  

## <a name="related-content"></a>См. также  
  
-   Видеоролик [Использование Microsoft Attunity Connector for Oracle для повышения производительности пакетов](https://technet.microsoft.com/sqlserver/gg598963.aspx)на сайте technet.microsoft.com  
  
-   Статьи Wiki [Сетевые соединения служб SSIS](https://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity)на сайте social.technet.microsoft.com  
  
-   Запись блога [Подключение к MySQL из SSIS](https://go.microsoft.com/fwlink/?LinkId=217669)на сайте blogs.msdn.com.  
  
-   Техническая статья [Извлечение и загрузка данных SharePoint в SQL Server Integration Services](https://go.microsoft.com/fwlink/?LinkId=247826)на сайте msdn.microsoft.com.  
  
-   Техническая статья [Получено сообщение об ошибке "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" при использовании диспетчера соединений Oracle в SSIS](https://go.microsoft.com/fwlink/?LinkId=233696) на сайте support.microsoft.com.  
  
  
