---
title: Создание базы данных служб Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d0c2a175b3d3288f9673044b88e7e62ac1a94f3a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Создайте базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , если для поддержки веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] требуется новая база данных.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Дополнительные сведения о требованиях, предъявляемых к компьютеру, на котором размещается база данных, см. в разделе [Требования баз данных (службы Master Data Services)](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
### <a name="to-create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services  
  
1.  Откройте среду [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните **Конфигурация базы данных**.  
  
3.  На странице **Конфигурация базы данных** выберите **Создать базу данных**.  
  
4.  Чтобы создать и настроить базу данных, выполните инструкции мастера **создания базы данных** . Дополнительные сведения о параметрах пользовательского интерфейса в мастере см. в разделе [Создание мастера баз данных (диспетчер конфигураций Master Data Services)](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
## <a name="next-steps"></a>Next Steps  
  
-   Настройте системные параметры базы данных и веб-приложения. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../master-data-services/system-settings-master-data-services.md).  
  
-   Создайте веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , которое будет связано с этой базой данных. Дополнительные сведения см. в статье [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Настройте план обслуживания для резервного копирования базы данных и журналов транзакций. Дополнительные сведения см. в разделе [Требования к базе данных (службы Master Data Services)](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
