---
title: Конструкторы запросов служб Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
caps.latest.revision: 16
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aed7304b4e7e48eff1691970da5ff68b03fd0962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222944"
---
# <a name="reporting-services-query-designers"></a>Конструкторы запросов служб Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] предоставляет графический и текстовый конструкторы запросов для построения запросов для каждого типа источника данных в отчете.  
  
 Некоторые источники данных поддерживают графические конструкторы запросов, которые позволяют формировать запросы в интерактивном режиме. Для других источников данных используется текстовый конструктор запросов. В графическом конструкторе запросов поддерживается перетаскивание из источника данных в область конструктора элементов метаданных, представляющих данные. В текстовом конструкторе запросов на панели запроса можно ввести текст команды. Переключение из графического конструктора запросов в текстовый производится щелчком значка текстового конструктора запросов на панели инструментов.  
  
 Доступные типы источников данных определяются модулями обработки данных служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], установленными на клиенте или на сервере отчетов. Дополнительные сведения см. в разделе [файл конфигурации RSReportDesigner](report-server/rsreportdesigner-configuration-file.md) и [файл конфигурации RSReportServer](report-server/rsreportserver-config-configuration-file.md).  
  
 Модуль обработки данных и связанный с ним конструктор запросов могут иметь различный уровень поддержки источников данных.  
  
-   **По типу конструктора запросов.** Например, источник данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает и графический и текстовый конструкторы запросов.  
  
-   **По версии языка запросов.** Например, язык запросов, такой как [!INCLUDE[tsql](../includes/tsql-md.md)] , может иметь разный синтаксис в зависимости от типа источника данных. Языки [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] и Oracle SQL имеют небольшие различия в синтаксисе команд запросов.  
  
-   **По поддержке указания схемы в именах объектов базы данных.** Если источник данных использует указание схемы в идентификаторе объекта базы данных, она должна указываться в запросе для всех имен, имеющих схему, отличную от схемы по умолчанию. Например, `SELECT FirstName, LastName FROM [Person].[Person]`.  
  
-   **По поддержке параметров запроса.** Поставщики данных поддерживают параметры запросов по-разному. Некоторые из них поддерживают именованные параметры, например: `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`. Другие поддерживают неименованные параметры, например: `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`. Идентификаторы параметров могут различаться для разных поставщиков данных. Так, в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используется символ "\@" , а в Oracle — двоеточие (:). Некоторые поставщики данных вообще не поддерживают параметров.  
  
-   **По возможности импортировать запросы.** Например, для источника данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно импортировать запросы из файла определения отчета (RDL) или из SQL-файла.  
  
## <a name="query-designers"></a>Конструкторы запросов  
 В следующих разделах описан пользовательский интерфейс каждого конструктора запросов.  
  
-   [Пользовательский интерфейс конструктора запросов многомерных выражений Analysis Services](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс конструктора запросов расширения интеллектуального анализа данных Analysis Services](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс графического конструктора запросов](report-data/graphical-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс конструктора реляционных запросов](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс конструктора запросов Hyperion Essbase](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс конструктора запросов моделей отчетов](report-data/report-model-query-designer-user-interface.md)  
  
-   [Пользовательский интерфейс конструктора запросов SAP NetWeaver BI](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [Конструктор запросов к спискам SharePoint](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [Пользовательский интерфейс текстового конструктора запросов](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>См. также  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Добавление данных из внешних источников данных &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md)   
 [Модули обработки данных и поставщики данных .NET Framework &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [Расширения &#40;SSRS&#41;](extensions-ssrs.md)  
  
  
