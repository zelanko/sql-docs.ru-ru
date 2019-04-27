---
title: Диалоговое окно "Создание веб-приложения" (диспетчер конфигурации служб Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.createapp.f1
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: dac7b74969c341b7f68c7dfbf56d2314d9ab4427
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765747"
---
# <a name="create-web-application-dialog-box-master-data-services-configuration-manager"></a>Диалоговое окно «Создание веб-приложения» (диспетчер конфигурации служб Master Data Services)
  С помощью диалогового окна **Создание веб-приложения** можно создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Это веб-приложение создается для сайта, выбранного на странице **Веб-конфигурация** .  
  
## <a name="web-application"></a>Веб-приложение  
 Веб-сервер обслуживает содержимое этого веб-приложения, используя папку [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **WebApplication** файловой системы. Ее местоположение указывается во время установки, и по умолчанию это *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.  
  
|Имя элемента управления|Описание|  
|------------------|-----------------|  
|Виртуальный путь|Выберите виртуальный путь к папке, в которой будет создано веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Виртуальный путь является частью URL-адреса, используемого для доступа к веб-приложению.<br /><br /> В этом списке отобраны только виртуальные пути, для которых может быть создано веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Нельзя создать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в другом веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
|Псевдоним|Введите имя веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или используйте имя, установленное по умолчанию. Это имя используется в URL-адресе для доступа к веб-приложению из веб-браузера.|  
  
## <a name="application-pool"></a>Пул приложений  
  
|Имя элемента управления|Описание|  
|------------------|-----------------|  
|**Name**|Введите уникальное и понятное имя для нового пула приложений или используйте предложенное по умолчанию. Веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] будет добавлено в этот пул приложений.<br /><br /> Пулы приложений определяют границы, которые не позволяют приложениям из одного пула мешать работе приложений из другого пула.|  
|**Имя пользователя**|Введите имя домена и пользователя из Active Directory. Эта учетная запись является идентификатором пула приложения, в котором выполняется веб-приложение. Эта учетная запись должна быть той же учетной записью службы, указанной при создании базы данных служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> С целью доступа к базе данных данная учетная запись добавляется к роли базы данных mds_exec в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Имена входа, пользователи и роли базы данных (службы Master Data Services)](database-logins-users-and-roles-master-data-services.md). Она также добавляется в группу Windows [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **MDS_ServiceAccounts**, которой предоставляется разрешение на доступ к временному каталогу компиляции **MDSTempDir** в файловой системе. Дополнительные сведения см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../../2014/master-data-services/folder-and-file-permissions-master-data-services.md).|  
|**Пароль**|Введите пароль для указанной учетной записи пользователя.|  
|**Подтверждение пароля**|Повторно введите пароль для указанной учетной записи пользователя. Поля **Пароль** и **Подтверждение пароля** должны содержать один и тот же пароль.|  
  
## <a name="see-also"></a>См. также  
 [Страница "Веб-конфигурация" (диспетчер конфигурации Master Data Services)](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)   
 [Настройка веб-сайта и базы данных для служб Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Веб-приложения требованиям &#40;службы Master Data Services&#41;](install-windows/web-application-requirements-master-data-services.md)   
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
