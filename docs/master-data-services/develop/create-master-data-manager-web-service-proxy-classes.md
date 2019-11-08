---
title: Создание классов-посредников веб-службы диспетчера основных данных
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1096da19a45e15ab2216cea2f4a4a38ecb05233e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729317"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Создание классов-посредников веб-службы диспетчера основных данных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Веб-служба [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] позволяет программно использовать функции [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с любого компьютера, имеющего доступ к веб-сайту [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Перед тем как писать код для доступа к веб-службе, необходимо создать классы-посредники. Основным классом-посредником, который используется для выполнения операций веб-службы, является класс <xref:Microsoft.MasterDataServices.ServiceClient>, реализующий интерфейс <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Включение публикации метаданных веб-службы  
 Перед созданием классов-посредников необходимо включить публикацию метаданных веб-службы. Для этого выполните следующие шаги.  
  
1.  Откройте файл Web.config [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в текстовом редакторе. Этот файл находится в папке WebApplication каталога пути установки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Найдите раздел **mdsWsHttpBehavior** в **\<serviceBehaviors>** . Для элемента **\<serviceMetadata>** присвойте параметру **httpGetEnabled** значение **true**.  
  
    > [!NOTE]  
    >  Чтобы включить веб-службы по протоколу SSL, задайте для свойства **httpsGetEnabled** значение **true** в разделе **mdsWsHttpBehavior** файла web.config. Необходимо также настроить **mdsWsHTTPBinding** для использования протокола SSL и закомментировать секцию не SSL.  
  
3.  Сохраните изменения в файле.  
  
4.  Для проверки публикации метаданных перейдите по URL-адресу службы, например: `https://yourserver/MDS/service/service.svc`. Если публикация метаданных включена, то на экране появится страница, которая начинается со слов   
    "Вы создали службу".  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Создание классов-посредников с помощью Visual Studio  
 Если установлена программа Visual Studio 2010, то самый простой способ создания прокси-классов заключается в добавлении в проект **Ссылки на службу**. Адресом ссылки на службу является URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], к которому добавлено /service/service.svc. Например: `https://yourserver/MDS/service/service.svc`. Дополнительные сведения см. в статье [Добавление, обновление или удаление ссылки на службу](https://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Создание классов-посредников с помощью Svcutil.exe  
 Средство Svcutil.exe устанавливается на компьютере при установке среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или пакета [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK. При использовании среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для выполнения команды необходимо использовать командную строку [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в статьях [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) (Служебная программа для работы с метаданными ServiceModel — Svcutil.exe) и [Generating a WCF Client from Service Metadata](https://go.microsoft.com/fwlink/?LinkId=164821) (Создание клиента WCF из метаданных службы).  
  
 Для создания набора классов-посредников C# с помощью Svcutil.exe используйте команду наподобие следующей:  
  
```  
svcutil.exe https://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Где:  
  
-   *servername*:*port* — это имя компьютера и номер порта компьютера, на котором размещаются службы [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *virtual_path* — это виртуальный путь к службам [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в службах Internet Information Services.  
  
-   *proxy_name* ― это имя создаваемого прокси-файла.  
  
## <a name="see-also"></a>См. также раздел  
 [Операции веб-службы по категориям (службы Master Data Services)](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
