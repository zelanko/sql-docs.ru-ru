---
title: "Создание прокси-классов веб-службы диспетчера основных данных | Документы Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d25fe8610e4518f3c2537ed50e523b468a908a0d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Создание классов-посредников веб-службы диспетчера основных данных
  Веб-служба [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] позволяет программно использовать функции [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с любого компьютера, имеющего доступ к веб-сайту [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Перед тем как писать код для доступа к веб-службе, необходимо создать классы-посредники. Основным классом-посредником, который используется для выполнения операций веб-службы, является класс <xref:Microsoft.MasterDataServices.ServiceClient>, реализующий интерфейс <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Включение публикации метаданных веб-службы  
 Перед созданием классов-посредников необходимо включить публикацию метаданных веб-службы. Для этого выполните следующие шаги.  
  
1.  Откройте файл Web.config [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в текстовом редакторе. Этот файл находится в папке WebApplication каталога пути установки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Найдите раздел **mdsWsHttpBehavior** в **\<serviceBehaviors>**. Для элемента **\<serviceMetadata>** присвойте параметру **httpGetEnabled** значение **true**.  
  
    > [!NOTE]  
    >  Чтобы включить веб-службы по протоколу SSL, задайте для свойства **httpsGetEnabled** значение **true** в разделе **mdsWsHttpBehavior** файла web.config. Необходимо также настроить **mdsWsHTTPBinding** для использования протокола SSL и закомментировать секцию не SSL.  
  
3.  Сохраните изменения в файле.  
  
4.  Для проверки публикации метаданных перейдите по URL-адресу службы, например: `http://yourserver/MDS/service/service.svc`. Если публикация метаданных включена, то на экране появится страница, которая начинается со слов   
    «Вы создали службу».  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Создание классов-посредников с помощью Visual Studio  
 Если установлена программа Visual Studio 2010, то самый простой способ создания прокси-классов заключается в добавлении в проект **Ссылки на службу**. Адресом ссылки на службу является URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], к которому добавлено /service/service.svc. Например: `http://yourserver/MDS/service/service.svc`. Дополнительные сведения см. в статье [Добавление, обновление или удаление ссылки на службу](http://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Создание классов-посредников с помощью Svcutil.exe  
 Средство Svcutil.exe устанавливается на компьютере при установке среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или пакета [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK. При использовании среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для выполнения команды необходимо использовать командную строку [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в статьях [ServiceModel Metadata Utility Tool (Svcutil.exe)](http://go.microsoft.com/fwlink/?LinkId=165027) (Служебная программа для работы с метаданными ServiceModel — Svcutil.exe) и [Generating a WCF Client from Service Metadata](http://go.microsoft.com/fwlink/?LinkId=164821) (Создание клиента WCF из метаданных службы).  
  
 Для создания набора классов-посредников C# с помощью Svcutil.exe используйте команду наподобие следующей:  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Где:  
  
-   *servername*:*port* — это имя компьютера и номер порта компьютера, на котором размещаются службы [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *virtual_path* — это виртуальный путь к службам [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в службах Internet Information Services.  
  
-   *proxy_name* ― это имя создаваемого прокси-файла.  
  
## <a name="see-also"></a>См. также:  
 [Операции веб-службы по категориям (службы Master Data Services)](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
