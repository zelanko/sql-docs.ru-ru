---
title: Справочник по веб-конфигурации (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 9c345312ddadab6c5efd689d36f36f09cc2d0a41
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250224"
---
# <a name="web-configuration-reference-master-data-services"></a>Раздел «Веб-конфигурация» (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] хранит в файле Web.config параметры конфигурации, которые позволяют службам IIS разместить веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и веб-службу. Этот файл Web.config находится в папке WebApplication пути установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о пути и разрешениях см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Элементы файла Web.Config  
 Помимо стандартных элементов настройки IIS, .NET Framework, ASP.NET и Windows Communication Foundation (WCF), в файле Web.config содержится пользовательский элемент [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — **\<masterDataServices>**. В следующей таблице описываются элементы, включенные в файл Web.config.  
  
|Элемент настройки|Описание|  
|---------------------------|-----------------|  
|`masterDataServices`|Пользовательский элемент. Соединяет веб-службу [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|`connectionStrings`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу connectionStrings в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178347) .|  
|`system.web`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178348) .|  
|`startup`|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<startup>](http://go.microsoft.com/fwlink/?LinkId=178349).|  
|`runtime`|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<runtime>](http://go.microsoft.com/fwlink/?LinkId=178350).|  
|`system.codedom`|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.codedom>](http://go.microsoft.com/fwlink/?LinkId=178351).|  
|`system.web.extensions`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web.extensions в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178352) .|  
|`system.webServer`|Группа разделов, содержащая элементы IIS. Дополнительные сведения см. в статье MSDN, посвященной [группе разделов system.webServer в \[схеме параметров IIS 7\]](http://go.microsoft.com/fwlink/?LinkId=178353).|  
|`system.serviceModel`|Элемент WCF-адреса. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.serviceModel>](http://go.microsoft.com/fwlink/?LinkId=178354).|  
|`system.diagnostics`|Элемент .NET Framework. Дополнительные сведения см. в статье MSDN, посвященной [элементу \<system.diagnostics>](http://go.microsoft.com/fwlink/?LinkId=178355).|  
|`appSettings`|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу appSettings в схеме общих параметров](http://go.microsoft.com/fwlink/?LinkId=178356) .|  
  
## <a name="masterdataservices-element"></a>Элемент masterDataServices  
 Элемент **\<masterDataServices>** является пользовательским и используется для соединения веб-службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
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
|`virtualPath`|Атрибут. Указывает виртуальный путь веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и службы. Это соответствует `path` атрибут  **\<приложения >** элемента под  **\<сайта >** в файле IIS ApplicationHost.config.|  
|`siteName`|Атрибут. Указывает имя сайта, на котором размещены веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и служба. Это соответствует `name` атрибут  **\<сайта >** элемента под  **\<сайты >** в файле IIS ApplicationHost.config.|  
|`connectionName`|Атрибут. Определяет имя соединения, которое будет использоваться. Это соответствует `name` атрибут  **\<Добавить >** элемента под  **\<connectionStrings >** элемент в файле Web.config.|  
|`serviceName`|Атрибут. Указывает имя веб-службы. Это соответствует `name` атрибут  **\<службы >** элемента под  **\<services >** элемент в файле Web.config.|  
  
### <a name="example"></a>Пример  
 В следующем примере показана служба с именем MDS1 на сайте Contoso и путь /MDS с использованием строки соединения, указанной MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
