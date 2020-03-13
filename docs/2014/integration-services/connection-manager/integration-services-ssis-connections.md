---
title: Соединения служб Integration Services (SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 18575c95602f73baa959d35b176cf16220fc8e64
ms.sourcegitcommit: 59c09dbe29882cbed539229a9bc1de381a5a4471
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79112166"
---
# <a name="integration-services-ssis-connections"></a>Соединения в службах Integration Services (SSIS)
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
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют диспетчер соединений в качестве логического представления соединения. На стадии разработки устанавливаются свойства диспетчера соединений, которые описывают физическое соединение, создаваемое сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] при выполнении пакета. Например, диспетчер соединений имеет свойство `ConnectionString`, устанавливаемое на стадии разработки. На стадии выполнения значение этого свойства используется для создания физического соединения.  
  
 Пакет может содержать несколько экземпляров диспетчера соединений одного типа, и для каждого из них свойства устанавливаются отдельно. На стадии выполнения каждый экземпляр диспетчера соединений создает соединение со своими атрибутами.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляет несколько типов диспетчеров соединений, которые позволяют пакету подключаться к различным источникам данных и серверам.  
  
-   Встроенные диспетчеры соединений, которые устанавливаются со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Диспетчеры соединений, которые можно загрузить на веб-сайте корпорации [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Можно создать собственный диспетчер соединений, если существующие диспетчеры не отвечают требованиям.  
  
### <a name="built-in-connection-managers"></a>Встроенные диспетчеры соединений  
 В следующей таблице перечислены типы диспетчеров соединений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляемые службами.  
  
|Тип|Description|Раздел|  
|----------|-----------------|-----------|  
|ADO|Подключается к объектам данных ActiveX (ADO).|[Диспетчер соединений ADO](ado-connection-manager.md)|  
|ADO.NET|Подключается к источнику данных при помощи поставщика .NET.|[Диспетчер соединений ADO.NET](ado-net-connection-manager.md)|  
|CACHE|Считывает данные из потока данных или из файла кэша (CAW) и может сохранять данные в файле кэша.|[диспетчер соединений с кэшем](cache-connection-manager.md)|  
|DQS|Подключается к серверу служб качества данных и базе данных служб Data Quality Services на сервере.|[Диспетчер соединений «Очистка DQS»](dqs-cleansing-connection-manager.md)|  
|EXCEL;|Подключается к файлу книги Excel.|[Диспетчер подключений Excel](excel-connection-manager.md)|  
|FILE|Подключается к файлу или папке.|[диспетчер соединения файлов](file-connection-manager.md)|  
|FLATFILE|Подключается к данным в отдельном неструктурированном файле.|[Диспетчер соединений с неструктурированными файлами](flat-file-connection-manager.md)|  
|FTP|Подключается к FTP-серверу.|[диспетчер FTP-соединений](ftp-connection-manager.md)|  
|HTTP|Подключается к веб-серверу.|[диспетчер HTTP-соединений](http-connection-manager.md)|  
|MSMQ|Подключается к очереди сообщений.|[диспетчер соединений MSMQ](msmq-connection-manager.md)|  
|MSOLAP100|Подключается к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекту.|[Диспетчер подключений Analysis Services](analysis-services-connection-manager.md)|  
|MULTIFILE|Подключается к нескольким файлам и папкам.|[диспетчер соединений с несколькими файлами](multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Подключается к нескольким файлам данных и папкам.|[диспетчер соединения с несколькими неструктурированными файлами](multiple-flat-files-connection-manager.md)|  
|OLEDB|Подключается к источнику данных при помощи поставщика OLE DB.|[диспетчер соединений OLE DB](ole-db-connection-manager.md)|  
|ODBC|Подключается к источнику данных через ODBC.|[диспетчер соединений ODBC](odbc-connection-manager.md)|  
|SMOServer|Подключается к серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).|[SMO, диспетчер соединений](smo-connection-manager.md)|  
|SMTP|Подключается к почтовому серверу SMTP.|[Диспетчер соединений SMTP](smtp-connection-manager.md)|  
|SQLMOBILE|Подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Диспетчер соединений SQL Server Compact Edition](sql-server-compact-edition-connection-manager.md)|  
|WMI|Подключается к серверу и определяет на нем область инструментария управления Windows (WMI).|[Диспетчер WMI-соединений](wmi-connection-manager.md)|  
  
### <a name="connection-managers-available-for-download"></a>Диспетчеры соединений, доступные для загрузки  
 В следующей таблице перечислены дополнительные типы диспетчеров соединений, которые вы можете загрузить с веб-сайта [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Перечисленные в следующей таблице диспетчеры соединений работают только с выпусками [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] и [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Тип|Description|Раздел|  
|----------|-----------------|-----------|  
|ORACLE|Подключается к \<сведениям о версии Oracle> сервере.|Диспетчер соединений Oracle — это компонент диспетчера соединений соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
|SAPBI|Подключается к системе SAP NetWeaver BI версии 7.|Диспетчер соединений SAP BI — это компонент диспетчера соединений соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Кроме того, в состав соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft SQL Server 2008 Feature Pack](https://www.microsoft.com/download/details.aspx?id=30440)(на английском языке).|  
|TERADATA|Подключается к \<сведениям о версии Teradata> сервере.|Диспетчер соединений Teradata — это компонент диспетчера соединений соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
  
### <a name="custom-connection-managers"></a>Пользовательские диспетчеры соединений  
 Кроме того, можно создавать пользовательские диспетчеры соединений. Дополнительные сведения см. в разделе [Developing a Custom Connection Manager](../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о добавлении или удалении диспетчера соединений в пакете см. в разделе [Добавление, удаление или совместное использование диспетчера соединений в пакете](../add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 Подробные сведения о задании свойств диспетчера соединений в пакете см. в разделе [Задание свойств диспетчера соединений](../set-the-properties-of-a-connection-manager.md).  
  
## <a name="related-content"></a>См. также  
  
-   Видеоролик [Использование Microsoft Attunity Connector for Oracle для повышения производительности пакетов](https://technet.microsoft.com/sqlserver/gg598963.aspx)на сайте technet.microsoft.com  
  
-   Статьи Wiki [Сетевые соединения служб SSIS](https://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity)на сайте social.technet.microsoft.com  
  
-   Запись блога [Подключение к MySQL из SSIS](https://go.microsoft.com/fwlink/?LinkId=217669)на сайте blogs.msdn.com.  
  
-   Техническая статья [Извлечение и загрузка данных SharePoint в SQL Server Integration Services](https://go.microsoft.com/fwlink/?LinkId=247826)на сайте msdn.microsoft.com.  
  
-   Техническая статья [Получено сообщение об ошибке "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" при использовании диспетчера соединений Oracle в SSIS](https://go.microsoft.com/fwlink/?LinkId=233696) на сайте support.microsoft.com.  
  
  
