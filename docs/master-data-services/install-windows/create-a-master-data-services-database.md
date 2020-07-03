---
title: Создание базы данных служб Master Data Services
description: Создайте базу данных Master Data Services, когда требуется новая база данных для поддержки диспетчер основных данных веб-приложения и веб-службы Master Data Services.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: af13d59ddb5c8837959feb83b31fc17dbcd7aa29
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883868"
---
# <a name="create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Создайте базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , если для поддержки веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] требуется новая база данных.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Дополнительные сведения о требованиях, предъявляемых к компьютеру, на котором размещается база данных, см. в разделе [Требования баз данных (службы Master Data Services)](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
### <a name="to-create-a-master-data-services-database"></a>Создание базы данных служб Master Data Services  
  
1.  Откройте [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните **Конфигурация базы данных**.  
  
3.  На странице **Конфигурация базы данных** выберите **Создать базу данных**.  
  
4.  Чтобы создать и настроить базу данных, выполните инструкции мастера **создания базы данных** . Дополнительные сведения о параметрах пользовательского интерфейса в мастере см. в разделе [Создание мастера баз данных (диспетчер конфигураций Master Data Services)](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
## <a name="next-steps"></a>Next Steps  
  
-   Настройте системные параметры базы данных и веб-приложения. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../master-data-services/system-settings-master-data-services.md).  
  
-   Создайте веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , которое будет связано с этой базой данных. Дополнительные сведения см. в статье [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Настройте план обслуживания для резервного копирования базы данных и журналов транзакций. Дополнительные сведения см. в разделе [Требования к базе данных (службы Master Data Services)](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
