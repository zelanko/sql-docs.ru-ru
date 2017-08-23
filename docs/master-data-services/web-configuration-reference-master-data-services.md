---
title: "Веб-ссылку конфигурации (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1be0e90d7d2ba9b2751677015957ca249d91119e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="web-configuration-reference-master-data-services"></a>Раздел «Веб-конфигурация» (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]использует файл Web.config содержит параметры конфигурации, которые позволяют Internet Information Services (IIS) для размещения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] веб-приложения и веб-службы. Этот файл Web.config находится в папке WebApplication пути установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о пути и разрешениях см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Элементы файла Web.Config  
 В файле Web.config содержится пользовательский [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] элемент,  **\<masterDataServices >**, помимо стандартных элементов настройки IIS, .NET Framework, ASP.NET и Windows Communication Foundation (WCF). В следующей таблице описываются элементы, включенные в файл Web.config.  
  
|Элемент настройки|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Пользовательский элемент. Соединяет веб-службу [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу connectionStrings в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178347) .|  
|**system.web**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178348) .|  
|**startup**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<запуска > элемент](http://go.microsoft.com/fwlink/?LinkId=178349) в библиотеке MSDN.|  
|**среда выполнения**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<среды выполнения > элемент](http://go.microsoft.com/fwlink/?LinkId=178350) в библиотеке MSDN.|  
|**system.codedom**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<system.codedom > элемент](http://go.microsoft.com/fwlink/?LinkId=178351) в библиотеке MSDN.|  
|**system.web.extensions**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу system.web.extensions в схеме параметров ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178352) .|  
|**system.webServer**|Группа разделов, содержащая элементы IIS. Дополнительные сведения см. в статье MSDN, посвященной [группе разделов system.webServer в \[схеме параметров IIS 7\]](http://go.microsoft.com/fwlink/?LinkId=178353).|  
|**system.serviceModel**|Элемент WCF-адреса. Дополнительные сведения см. в разделе [ \<system.serviceModel >](http://go.microsoft.com/fwlink/?LinkId=178354) в библиотеке MSDN.|  
|**system.diagnostics**|Элемент .NET Framework. Дополнительные сведения см. в разделе [ \<system.diagnostics > элемент](http://go.microsoft.com/fwlink/?LinkId=178355) в библиотеке MSDN.|  
|**appSettings**|Элемент ASP.NET. Дополнительные сведения см. в статье MSDN, посвященной [элементу appSettings в схеме общих параметров](http://go.microsoft.com/fwlink/?LinkId=178356) .|  
  
## <a name="masterdataservices-element"></a>Элемент masterDataServices  
  **\<MasterDataServices >** элемент является пользовательским элементом, используемый для подключения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] веб-службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных.  
  
### <a name="syntax"></a>Синтаксис  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Элементы и атрибуты  
  
|Элемент|Description|  
|----------|-----------------|  
|**instance**|Дочерний элемент. Содержит атрибуты, указывающие данные для веб-службы и строки подключения к базе данных.|  
|**virtualPath**|Атрибут. Указывает виртуальный путь веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и службы. Это соответствует **путь** атрибут  **\<приложения >** элемента под  **\<сайта >** в файле IIS ApplicationHost.config.|  
|**siteName**|Атрибут. Указывает имя сайта, на котором размещены веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] и служба. Это соответствует **имя** атрибут  **\<сайта >** элемента под  **\<сайтов >** в файле IIS ApplicationHost.config.|  
|**connectionName**|Атрибут. Определяет имя соединения, которое будет использоваться. Это соответствует **имя** атрибут  **\<Добавить >** элемента под  **\<connectionStrings >** элемента в файле Web.config.|  
|**serviceName**|Атрибут. Указывает имя веб-службы. Это соответствует **имя** атрибут  **\<службы >** элемента под  **\<services >** элемента в файле Web.config.|  
  
### <a name="example"></a>Пример  
 В следующем примере показана служба с именем MDS1 на сайте Contoso и путь /MDS с использованием строки соединения, указанной MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
