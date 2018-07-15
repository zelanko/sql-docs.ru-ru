---
title: Соединения служб Integration Services (SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
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
caps.latest.revision: 90
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 30a226221234b6668a50f6feef2e61e3b5a38f6c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273290"
---
# <a name="integration-services-ssis-connections"></a>Соединения в службах Integration Services (SSIS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют соединения для выполнения различных задач и реализации функций служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
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
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют диспетчер соединений в качестве логического представления соединения. На стадии разработки устанавливаются свойства диспетчера соединений, которые описывают физическое соединение, создаваемое сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] при выполнении пакета. Например, диспетчер соединений имеет `ConnectionString` свойство, которое можно задать во время разработки; во время выполнения, физическое подключение создается с использованием значения в свойство строки подключения.  
  
 Пакет может содержать несколько экземпляров диспетчера соединений одного типа, и для каждого из них свойства устанавливаются отдельно. На стадии выполнения каждый экземпляр диспетчера соединений создает соединение со своими атрибутами.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют несколько типов диспетчеров соединений, которые позволяют пакету подключаться к различным источникам данных и серверам.  
  
-   Встроенные диспетчеры соединений, которые устанавливаются со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Диспетчеры соединений, которые можно загрузить на веб-сайте корпорации [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Можно создать собственный диспетчер соединений, если существующие диспетчеры не отвечают требованиям.  
  
### <a name="built-in-connection-managers"></a>Встроенные диспетчеры соединений  
 В следующей таблице перечислены типы диспетчеров соединений, предоставляемые службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
|Тип|Описание|Раздел|  
|----------|-----------------|-----------|  
|ADO|Подключается к объектам данных ActiveX (ADO).|[Диспетчер подключений объектов данных ActiveX](ado-connection-manager.md)|  
|ADO.NET|Подключается к источнику данных при помощи поставщика .NET.|[Диспетчер подключений ADO.NET](ado-net-connection-manager.md)|  
|CACHE|Считывает данные из потока данных или из файла кэша (CAW) и может сохранять данные в файле кэша.|[Диспетчер подключений с кэшем](cache-connection-manager.md)|  
|DQS|Подключается к серверу служб качества данных и базе данных служб Data Quality Services на сервере.|[Диспетчер подключений "Очистка DQS"](dqs-cleansing-connection-manager.md)|  
|EXCEL|Подключается к файлу книги Excel.|[Диспетчер подключений Excel](excel-connection-manager.md)|  
|FILE|Подключается к файлу или папке.|[Диспетчер подключений файлов](file-connection-manager.md)|  
|FLATFILE|Подключается к данным в отдельном неструктурированном файле.|[Диспетчер подключений неструктурированных файлов](flat-file-connection-manager.md)|  
|FTP|Подключается к FTP-серверу.|[Диспетчер FTP-подключений](ftp-connection-manager.md)|  
|HTTP|Подключается к веб-серверу.|[Диспетчер HTTP-подключений](http-connection-manager.md)|  
|MSMQ|Подключается к очереди сообщений.|[Диспетчер подключений MSMQ](msmq-connection-manager.md)|  
|MSOLAP100|Подключается к экземпляру служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|[Диспетчер подключений служб Analysis Services](analysis-services-connection-manager.md)|  
|MULTIFILE|Подключается к нескольким файлам и папкам.|[Диспетчер подключений нескольких файлов](multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Подключается к нескольким файлам данных и папкам.|[Диспетчер подключений нескольких неструктурированных файлов](multiple-flat-files-connection-manager.md)|  
|OLEDB|Подключается к источнику данных при помощи поставщика OLE DB.|[Диспетчер подключений OLE DB](ole-db-connection-manager.md)|  
|интерфейс ODBC|Подключается к источнику данных через ODBC.|[Диспетчер подключений ODBC](odbc-connection-manager.md)|  
|SMOServer|Подключается к серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).|[Диспетчер подключений управляющих объектов SQL Server](smo-connection-manager.md)|  
|SMTP|Подключается к почтовому серверу SMTP.|[Диспетчер SMTP-подключений](smtp-connection-manager.md)|  
|SQLMOBILE|Подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|[Диспетчер подключений SQL Server Compact Edition](sql-server-compact-edition-connection-manager.md)|  
|WMI|Подключается к серверу и определяет на нем область инструментария управления Windows (WMI).|[Диспетчер WMI-подключений](wmi-connection-manager.md)|  
  
### <a name="connection-managers-available-for-download"></a>Диспетчеры соединений, доступные для загрузки  
 В следующей таблице перечислены дополнительные типы диспетчеров соединений, которые вы можете загрузить с веб-сайта [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
> [!IMPORTANT]  
>  Перечисленные в следующей таблице диспетчеры соединений работают только с выпусками [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] и [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|Тип|Описание|Раздел|  
|----------|-----------------|-----------|  
|ORACLE|Подключается к Oracle \<сведений о версии > server.|Диспетчер соединений Oracle — это компонент диспетчера соединений соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Oracle [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
|SAPBI|Подключается к системе SAP NetWeaver BI версии 7.|Диспетчер соединений SAP BI — это компонент диспетчера соединений соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Кроме того, в состав соединителя для SAP BI [!INCLUDE[msCoName](../../includes/msconame-md.md)] входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft SQL Server 2008 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=262016)(на английском языке).|  
|TERADATA|Подключается к Teradata \<сведений о версии > server.|Диспетчер соединений Teradata — это компонент диспетчера соединений соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity. Кроме того, в состав соединителя для Teradata [!INCLUDE[msCoName](../../includes/msconame-md.md)] компании Attunity входят источник и назначение. Дополнительные сведения см. на странице загрузки [Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526)(на английском языке).|  
  
### <a name="custom-connection-managers"></a>Пользовательские диспетчеры соединений  
 Кроме того, можно создавать пользовательские диспетчеры соединений. Дополнительные сведения см. в разделе [Developing a Custom Connection Manager](../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о добавлении или удалении диспетчера соединений в пакете см. в разделе [Добавление, удаление или совместное использование диспетчера соединений в пакете](../add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 Подробные сведения о задании свойств диспетчера соединений в пакете см. в разделе [Задание свойств диспетчера соединений](../set-the-properties-of-a-connection-manager.md).  
  
## <a name="related-content"></a>См. также  
  
-   Видеоролик [Использование Microsoft Attunity Connector for Oracle для повышения производительности пакетов](http://technet.microsoft.com/sqlserver/gg598963.aspx)на сайте technet.microsoft.com  
  
-   Статьи Wiki [Сетевые соединения служб SSIS](http://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity)на сайте social.technet.microsoft.com  
  
-   Запись блога [Подключение к MySQL из SSIS](http://go.microsoft.com/fwlink/?LinkId=217669)на сайте blogs.msdn.com.  
  
-   Техническая статья [Извлечение и загрузка данных SharePoint в SQL Server Integration Services](http://go.microsoft.com/fwlink/?LinkId=247826)на сайте msdn.microsoft.com.  
  
-   Техническая статья [Получено сообщение об ошибке "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" при использовании диспетчера соединений Oracle в SSIS](http://go.microsoft.com/fwlink/?LinkId=233696)на сайте support.microsoft.com.  
  
  
