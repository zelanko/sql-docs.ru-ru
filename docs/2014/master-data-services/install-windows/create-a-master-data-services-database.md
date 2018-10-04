---
title: Создание базы данных служб Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 11fb8139c674a165607f08551d6333eff534ebac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158294"
---
# <a name="create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services
  Создайте базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , если для поддержки веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] требуется новая база данных.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Дополнительные сведения о требованиях, предъявляемых к компьютеру, на котором размещается база данных, см. в разделе [Требования баз данных (службы Master Data Services)](database-requirements-master-data-services.md).  
  
### <a name="to-create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните **Конфигурация базы данных**.  
  
3.  На странице **Конфигурация базы данных** выберите **Создать базу данных**.  
  
4.  Чтобы создать и настроить базу данных, выполните инструкции мастера **создания базы данных** . Дополнительные сведения о параметрах пользовательского интерфейса в мастере см. в разделе [Создание мастера баз данных (диспетчер конфигураций Master Data Services)](../create-database-wizard-master-data-services-configuration-manager.md).  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Настройте системные параметры базы данных и веб-приложения. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../system-settings-master-data-services.md).  
  
-   Создайте веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , которое будет связано с этой базой данных. Дополнительные сведения см. в статье [Создание веб-приложения мастера основных данных (службы Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Настройте план обслуживания для резервного копирования базы данных и журналов транзакций. Дополнительные сведения см. в разделе [Требования к базе данных (службы Master Data Services)](database-requirements-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](install-master-data-services.md)  
  
  
