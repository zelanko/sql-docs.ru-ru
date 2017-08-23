---
title: "Создание классов-посредников веб-службы диспетчера основных данных | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a45cd15ced90aef95feb03f8fbaafd5aa70cb746
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Создание классов-посредников веб-службы диспетчера основных данных
  Веб-служба [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] позволяет программно использовать функции [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с любого компьютера, имеющего доступ к веб-сайту [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Перед тем как писать код для доступа к веб-службе, необходимо создать классы-посредники. Основным классом-посредником, который используется для выполнения операций веб-службы, является класс <xref:Microsoft.MasterDataServices.ServiceClient>, реализующий интерфейс <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Включение публикации метаданных веб-службы  
 Перед созданием классов-посредников необходимо включить публикацию метаданных веб-службы. Для этого выполните следующие шаги.  
  
1.  Откройте [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] файл Web.config в текстовом редакторе. Этот файл находится в папке WebApplication каталога пути установки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Найти **mdsWsHttpBehavior** раздела  **\<serviceBehaviors >**. Для  **\<serviceMetadata >** , задайте **httpGetEnabled** для **true**.  
  
    > [!NOTE]  
    >  Если вы хотите включить веб-служб через Secure Sockets Layer (SSL), установите **httpsGetEnabled** для **true** в **mdsWsHttpBehavior** раздел файла web.config. Необходимо также изменить **mdsWsHTTPBinding** , чтобы он настроен для SSL, а также и закомментировать секцию не SSL.  
  
3.  Сохраните изменения в файле.  
  
4.  Проверьте публикацию метаданных, перейдя в URL-адрес службы, например: `http://yourserver/MDS/service/service.svc`. Если публикация метаданных включена, то на экране появится страница, которая начинается со слов   
    «Вы создали службу».  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Создание классов-посредников с помощью Visual Studio  
 Если установлена Visual Studio 2010, самый простой способ создать классы-посредники является добавление **ссылки на службу** в проект. Адресом ссылки на службу является URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], к которому добавлено /service/service.svc. Например: `http://yourserver/MDS/service/service.svc`. Дополнительные сведения см. в разделе [как: Добавление, обновление или удаление ссылки на службу](http://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Создание классов-посредников с помощью Svcutil.exe  
 Должен иметь либо [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] установки Windows SDK, чтобы получить Svcutil.exe на локальном компьютере. При использовании среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для выполнения команды необходимо использовать командную строку [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [ServiceModel Metadata Utility Tool (Svcutil.exe)](http://go.microsoft.com/fwlink/?LinkId=165027) и [создание клиента WCF из метаданных службы](http://go.microsoft.com/fwlink/?LinkId=164821).  
  
 Для создания набора классов-посредников C# с помощью Svcutil.exe используйте команду наподобие следующей:  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Где:  
  
-   *ServerName*:*порт* — это имя компьютера и номер компьютера, на котором размещена порта [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *virtual_path* виртуальный путь к [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в Internet Information Services (IIS).  
  
-   *proxy_name* — это имя для создаваемого файла посредника.  
  
## <a name="see-also"></a>См. также:  
 [Операции по категориям веб-службы &#40; Службы Master Data Services &#41;](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
