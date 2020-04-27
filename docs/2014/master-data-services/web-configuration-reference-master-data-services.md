---
title: Справочник по веб-конфигурации (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3582e7de37b99cd7f665f563e789259954b722
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65478487"
---
# <a name="web-configuration-reference-master-data-services"></a>Раздел «Веб-конфигурация» (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] хранит в файле Web.config параметры конфигурации, которые позволяют службам IIS разместить веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и веб-службу. Этот файл Web.config находится в папке WebApplication пути установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о пути и разрешениях см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Элементы файла Web.Config  
 В дополнение к стандартным элементам конфигурации IIS [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , .NET Framework, ASP.NET и Windows Communication Foundation (WCF) файл Web. config содержит пользовательский элемент ** \<masterDataServices>**. В следующей таблице описываются элементы, включенные в файл Web.config.  
  
|Элемент настройки|Описание|  
|---------------------------|-----------------|  
|`masterDataServices`|Пользовательский элемент. Соединяет веб-службу [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|`connectionStrings`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу connectionStrings в схеме параметров ASP.NET](https://go.microsoft.com/fwlink/?LinkId=178347) .|  
|`system.web`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web в схеме параметров ASP.NET](https://go.microsoft.com/fwlink/?LinkId=178348) .|  
|`startup`|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<элемент Startup>](https://go.microsoft.com/fwlink/?LinkId=178349) в библиотеке MSDN.|  
|`runtime`|Элемент .NET Framework. Дополнительные сведения см [ \<. в статье элемент> среды выполнения](https://go.microsoft.com/fwlink/?LinkId=178350) в библиотеке MSDN.|  
|`system.codedom`|Элемент .NET Framework. Дополнительные сведения см [ \<. в статье элемент System. CodeDom>](https://go.microsoft.com/fwlink/?LinkId=178351) в библиотеке MSDN.|  
|`system.web.extensions`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web.extensions в схеме параметров ASP.NET](https://go.microsoft.com/fwlink/?LinkId=178352) .|  
|`system.webServer`|Группа разделов, содержащая элементы IIS. Дополнительные сведения см. в статье MSDN, посвященной [группе разделов system.webServer в \[схеме параметров IIS 7\]](https://go.microsoft.com/fwlink/?LinkId=178353).|  
|`system.serviceModel`|Элемент WCF-адреса. Дополнительные сведения см. в разделе [ \<System. ServiceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) в библиотеке MSDN.|  
|`system.diagnostics`|Элемент .NET Framework. Дополнительные сведения см [ \<. в статье элемент System. Diagnostics>](https://go.microsoft.com/fwlink/?LinkId=178355) в библиотеке MSDN.|  
|`appSettings`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу appSettings в схеме общих параметров](https://go.microsoft.com/fwlink/?LinkId=178356) .|  
  
## <a name="masterdataservices-element"></a>Элемент masterDataServices  
 Элемент ** \<>masterDataServices** — это пользовательский элемент, который используется для подключения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] веб-службы к [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных.  
  
### <a name="syntax"></a>Синтаксис  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Элементы и атрибуты  
  
|Элемент|Описание|  
|----------|-----------------|  
|`instance`|Дочерний элемент. Содержит атрибуты, указывающие данные для веб-службы и строки подключения к базе данных.|  
|`virtualPath`|Атрибут. Указывает виртуальный путь веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и службы. Это соответствует `path` атрибуту элемента ** \<Application>** в элементе ** \<>сайта** в файле IIS ApplicationHost. config.|  
|`siteName`|Атрибут. Указывает имя сайта, на котором размещены веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и служба. Это соответствует `name` атрибуту элемента ** \<>сайта** в разделе ** \<Sites>** в файле IIS ApplicationHost. config.|  
|`connectionName`|Атрибут. Определяет имя соединения, которое будет использоваться. Это соответствует `name` атрибуту элемента ** \<Add>** в элементе ** \<ConnectionString>** в файле Web. config.|  
|`serviceName`|Атрибут. Указывает имя веб-службы. Это соответствует `name` атрибуту элемента ** \<Service>** в элементе ** \<служб>** в файле Web. config.|  
  
### <a name="example"></a>Пример  
 В следующем примере показана служба с именем MDS1 на сайте Contoso и путь /MDS с использованием строки соединения, указанной MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
