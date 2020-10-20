---
description: Раздел «Веб-конфигурация» (службы Master Data Services)
title: Раздел «Веб-конфигурация»
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7f4baf9f3ef626f5e2dcdc62092afaf1e586df33
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196098"
---
# <a name="web-configuration-reference-master-data-services"></a>Раздел «Веб-конфигурация» (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] хранит в файле Web.config параметры конфигурации, которые позволяют службам IIS разместить веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и веб-службу. Этот файл Web.config находится в папке WebApplication пути установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о пути и разрешениях см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Элементы файла Web.Config  
 Файл Web.config содержит пользовательский [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] элемент, **\<masterDataServices>** в дополнение к стандартным ЭЛЕМЕНТАМ конфигурации IIS, .NET Framework, ASP.NET и Windows Communication Foundation (WCF). В следующей таблице описываются элементы, включенные в файл Web.config.  
  
|Элемент настройки|Описание|  
|---------------------------|-----------------|  
|**masterDataServices**|Пользовательский элемент. Соединяет веб-службу [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу connectionStrings в схеме параметров ASP.NET](/previous-versions/dotnet/netframework-4.0/bf7sd233(v=vs.100)) .|  
|**System. Web**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web в схеме параметров ASP.NET](/previous-versions/dotnet/netframework-4.0/dayb112d(v=vs.100)) .|  
|**запуска**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<startup> элемент](/dotnet/framework/configure-apps/file-schema/startup/startup-element) в библиотеке MSDN.|  
|**Среда выполнения**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<runtime> элемент](/dotnet/framework/configure-apps/file-schema/runtime/runtime-element) в библиотеке MSDN.|  
|**system.codedom**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<system.codedom> элемент](/dotnet/framework/configure-apps/file-schema/compiler/system-codedom-element) в библиотеке MSDN.|  
|**System. Web. Extensions**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web.extensions в схеме параметров ASP.NET](/previous-versions/dotnet/netframework-4.0/bb546044(v=vs.100)) .|  
|**system.webServer**|Группа разделов, содержащая элементы IIS. Дополнительные сведения см. в статье MSDN, посвященной [группе разделов system.webServer в \[схеме параметров IIS 7\]](/previous-versions/iis/settings-schema/ms689429(v=vs.90)).|  
|**system.serviceModel**|Элемент WCF-адреса. Дополнительные сведения см [\<system.serviceModel>](/dotnet/framework/configure-apps/file-schema/wcf/system-servicemodel) . в разделе библиотеки MSDN.|  
|**system.diagnostics**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<system.diagnostics> элемент](/dotnet/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element) в библиотеке MSDN.|  
|**appSettings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу appSettings в схеме общих параметров](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) .|  
  
## <a name="masterdataservices-element"></a>Элемент masterDataServices  
 **\<masterDataServices>** Элемент является пользовательским элементом, который используется для подключения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] веб-службы к [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базе данных.  
  
### <a name="syntax"></a>Синтаксис  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Элементы и атрибуты  
  
|Элемент|Описание|  
|----------|-----------------|  
|**instance**|Дочерний элемент. Содержит атрибуты, указывающие данные для веб-службы и строки подключения к базе данных.|  
|**virtualPath**|Атрибут. Указывает виртуальный путь веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и службы. Соответствует атрибуту **path** **\<application>** элемента **\<site>** в ЭЛЕМЕНТЕ в файле ApplicationHost.config IIS.|  
|**Значением**|Атрибут. Указывает имя сайта, на котором размещены веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и служба. Соответствует атрибуту **Name** **\<site>** элемента **\<sites>** в файле ApplicationHost.config IIS.|  
|**connectionName**|Атрибут. Определяет имя соединения, которое будет использоваться. Соответствует атрибуту **Name** **\<add>** элемента **\<connectionStrings>** в Web.config.|  
|**Служба**|Атрибут. Указывает имя веб-службы. Соответствует атрибуту **Name** **\<service>** элемента **\<services>** в Web.config.|  
  
### <a name="example"></a>Пример  
 В следующем примере показана служба с именем MDS1 на сайте Contoso и путь /MDS с использованием строки соединения, указанной MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
