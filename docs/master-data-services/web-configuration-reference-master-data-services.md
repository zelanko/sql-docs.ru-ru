---
title: "Раздел &#171;Веб-конфигурация&#187; (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "файл веб-конфигурации [службы Master Data Services]"
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Раздел &#171;Веб-конфигурация&#187; (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] хранит в файле Web.config параметры конфигурации, которые позволяют службам IIS разместить веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и веб-службу. Этот файл Web.config находится в папке WebApplication пути установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о пути и разрешениях см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## Элементы файла Web.Config  
 Помимо стандартных элементов настройки IIS, .NET Framework, ASP.NET и Windows Communication Foundation (WCF), в файле Web.config содержится пользовательский элемент [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — **\<masterDataServices>**. В следующей таблице описываются элементы, включенные в файл Web.config.  
  
|Элемент настройки|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Пользовательский элемент. Соединяет веб-службу [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу connectionStrings в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178347).|  
|**system.web**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178348).|  
|**startup**|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<startup>](http://go.microsoft.com/fwlink/?LinkId=178349).|  
|**среда выполнения**|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<runtime>](http://go.microsoft.com/fwlink/?LinkId=178350).|  
|**system.codedom**|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.codedom>](http://go.microsoft.com/fwlink/?LinkId=178351).|  
|**system.web.extensions**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web.extensions в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178352).|  
|**system.webServer**|Группа разделов, содержащая элементы IIS. Дополнительные сведения см. в статье MSDN, посвященной [группе разделов system.webServer в \[схеме параметров IIS 7\]](http://go.microsoft.com/fwlink/?LinkId=178353).|  
|**system.serviceModel**|Элемент WCF-адреса. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.serviceModel>](http://go.microsoft.com/fwlink/?LinkId=178354).|  
|**system.diagnostics**|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.diagnostics>](http://go.microsoft.com/fwlink/?LinkId=178355).|  
|**appSettings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу appSettings в схеме общих параметров](http://go.microsoft.com/fwlink/?LinkId=178356).|  
  
## Элемент masterDataServices  
 Элемент **\<masterDataServices>** является пользовательским элементом, используемым для соединения веб-службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
### Синтаксис  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### Элементы и атрибуты  
  
|Элемент|Description|  
|----------|-----------------|  
|**instance**|Дочерний элемент. Содержит атрибуты, указывающие данные для веб-службы и строки подключения к базе данных.|  
|**virtualPath**|Атрибут. Указывает виртуальный путь веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и службы. Соответствует атрибуту **path** элемента **\<application>** в элементе **\<site>** файла IIS ApplicationHost.config.|  
|**siteName**|Атрибут. Указывает имя сайта, на котором размещены веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и служба. Соответствует атрибуту **name** элемента **\<site>** в элементе **\<sites>** файла IIS ApplicationHost.config.|  
|**connectionName**|Атрибут. Определяет имя соединения, которое будет использоваться. Соответствует атрибуту **name** элемента **\<add>** в элементе **\<connectionStrings>** файла Web.config.|  
|**serviceName**|Атрибут. Указывает имя веб-службы. Соответствует атрибуту **name** элемента **\<service>** в элементе **\<services>** файла Web.config.|  
  
### Пример  
 В следующем примере показана служба с именем MDS1 на сайте Contoso и путь /MDS с использованием строки соединения, указанной MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  