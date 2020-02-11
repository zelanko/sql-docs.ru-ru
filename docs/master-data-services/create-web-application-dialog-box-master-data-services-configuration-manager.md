---
title: Диалоговое окно «Создание веб-приложения»
ms.custom: seo-lt-2019
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql13.mds.configmanager.createapp.f1
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b35c47704915ec9e85f0c4f2ac083bfb7a6017ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729503"
---
# <a name="create-web-application-dialog-box-master-data-services-configuration-manager"></a>Диалоговое окно «Создание веб-приложения» (диспетчер конфигурации служб Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  С помощью диалогового окна **Создание веб-приложения** можно создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Это веб-приложение создается для сайта, выбранного на странице **Веб-конфигурация** .  
  
## <a name="web-application"></a>Веб-приложение  
 Веб-сервер обслуживает содержимое этого веб-приложения, используя папку [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **WebApplication** файловой системы. Ее местоположение указывается при установке; по умолчанию это *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|Виртуальный путь|Выберите виртуальный путь к папке, в которой будет создано веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Виртуальный путь является частью URL-адреса, используемого для доступа к веб-приложению.<br /><br /> В этом списке отобраны только виртуальные пути, для которых может быть создано веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Нельзя создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в другом веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
|Alias|Введите имя веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или используйте имя, установленное по умолчанию. Это имя используется в URL-адресе для доступа к веб-приложению из веб-браузера.|  
  
## <a name="application-pool"></a>Пул приложений  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Название**|Введите уникальное и понятное имя для нового пула приложений или используйте предложенное по умолчанию. Веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] будет добавлено в этот пул приложений.<br /><br /> Пулы приложений определяют границы, которые не позволяют приложениям из одного пула мешать работе приложений из другого пула.|  
|**User name**|Введите имя домена и пользователя из Active Directory. Эта учетная запись является идентификатором пула приложения, в котором выполняется веб-приложение. Эта учетная запись должна быть той же учетной записью службы, указанной при создании базы данных служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> С целью доступа к базе данных данная учетная запись добавляется к роли базы данных mds_exec в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Имена входа, пользователи и роли базы данных (службы Master Data Services)](../master-data-services/database-logins-users-and-roles-master-data-services.md). Она также добавляется в группу Windows [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**MDS_ServiceAccounts**, которой предоставляется разрешение на доступ к временному каталогу компиляции **MDSTempDir**в файловой системе. Дополнительные сведения см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../master-data-services/folder-and-file-permissions-master-data-services.md).|  
|**Пароль**|Введите пароль для указанной учетной записи пользователя.|  
|**Подтверждение пароля**|Повторно введите пароль для указанной учетной записи пользователя. Поля **Пароль** и **Подтверждение пароля** должны содержать один и тот же пароль.|  
  
## <a name="see-also"></a>См. также:  
 [Страница веб-конфигурации &#40;диспетчер конфигурации Master Data Services&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)   
Master Data Services [требования к веб-приложению](../master-data-services/install-windows/web-application-requirements-master-data-services.md) по [установке и настройке](../master-data-services/master-data-services-installation-and-configuration.md) &#40;Master Data Services&#41;   
 [Создание диспетчер основных данных &#40;веб-приложения Master Data Services&#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
