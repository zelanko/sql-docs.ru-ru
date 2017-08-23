---
title: "Связывание базы данных служб Master Data Services и веб-приложения | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 729f1dab03952ff2986973ec387b10a8f14a965f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="associate-a-master-data-services-database-and-web-application"></a>Связывание базы данных служб Master Data Services и веб-приложения
  Чтобы указать базу данных, используемую для веб-операций, нужно связать веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] с базой данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]должен быть установлен на локальном компьютере. Дополнительные сведения см. в статье [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).  
  
-   Должно существовать локальное веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Дополнительные сведения см. в статье [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Должна существовать локальная или удаленная база данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в статье [Создание базы данных служб Master Data Services](../../master-data-services/install-windows/create-a-master-data-services-database.md).  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a>Связывание базы данных служб Master Data Services и веб-приложения  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  В списке **Веб-сайт** раздела **Веб-приложение**страницы **Веб-конфигурация** выберите веб-сайт, на котором размещено веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
4.  В поле **Веб-приложение** выберите веб-приложение, в котором размещается [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
5.  В разделе **Связь приложения с базой данных**щелкните элемент **Выбрать**. Откроется диалоговое окно **Подключение к базе данных** .  
  
6.  Укажите сведения о соединении для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена база данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , и щелкните **Соединить**.  
  
7.  В списке **База данных служб Master Data Services** выберите базу данных, которую нужно связать с веб-приложением, и нажмите кнопку **ОК**.  
  
8.  В разделе **Связь приложения с базой данных**удостоверьтесь, что сведения об экземпляре и базе данных верны, а затем нажмите кнопку **Применить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Программный доступ к веб-службам [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] автоматически включается после создания веб-приложения. Включите публикацию метаданных, чтобы разработчики могли обращаться к метаданным служб и легко создавать классы-посредники для программного доступа. Дополнительные сведения см. в статье [Create Master Data Manager Web Service Proxy Classes](../../master-data-services/develop/create-master-data-manager-web-service-proxy-classes.md).  
  
-   Добавьте пользователей и группы в [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Если ни одной группе или пользователю не предоставлен доступ к [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], необходимо открыть [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , используя учетные данные системного администратора среды [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в статьях [Администраторы (службы Master Data Services)](../../master-data-services/administrators-master-data-services.md) и [Пользователи и группы (службы Master Data Services)](../../master-data-services/users-and-groups-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Конфигурация веб-страницу &#40; Диспетчер конфигурации Master Data Services &#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  
