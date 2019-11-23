---
title: Удаление служб Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 3909d6adb64b798fa17926620a7e7bd5914bf504
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952682"
---
# <a name="uninstall-reporting-services"></a>Удаление служб Reporting Services
  Удаление [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не приводит к удалению созданного содержимого или измененной конфигурации. Но если имеется содержимое, которое потребуется после завершения удаления, то рекомендуется создать копии содержимого до начала процесса удаления.  
  
## <a name="uninstall-sharepoint-mode"></a>Удаление режима интеграции с SharePoint  
 При удалении служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , работающих в режиме интеграции с SharePoint, будут удалены следующие компоненты:  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и прокси-сервер службы.  
  
-   Файлы, используемые для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не удаляются. Если данные приложения службы больше не требуются, удалите их с помощью центра администрирования Windows PowerShell или SharePoint.  
  
 Элементы отчетов и связанные с ними метаданные не удаляются. Эти сведения находятся в базах данных содержимого и конфигурации, связанных с приложениями служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Базы данных не удаляются, и можно вручную переместить базы данных в другую установку [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint. Если эта информация больше не требуется, удалите базы данных. Дополнительные сведения см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Далее приводятся примеры имен трех баз данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые не будут удалены.  
  
-   **База данных сервера отчетов:** ReportingService_7f616e2d253040e8ab5653b3c09a065e  
  
-   **Временная база данных сервера отчетов:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB  
  
-   **База данных предупреждений сервера отчетов:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting  
  
### <a name="uninstall-the-add-in-for-sharepoint-products"></a>Удаление надстройки для продуктов SharePoint.  
 При удалении надстройки с компьютера вы можете выбрать удаление только файлов или удаление и самого компонента [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из фермы. Сведения об удалении надстройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint см. [в статье Установка и удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
## <a name="uninstall-native-mode"></a>Удаление собственного режима  
 При удалении собственного режима служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] все, что было **создано** или **изменено** после установки, будет сохранено. В качестве примера можно назвать файлы базы данных, файлы журнала, файлы конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и элементы содержимого, такие как отчеты и файлы источников данных.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] представляет собой функцию экземпляра, поэтому не перечисляется на панели управления Windows «Программы и компоненты». Удаление собственного режима [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
1.  На панели управления Windows щелкните **Программы и компоненты**.  
  
2.  В окне **Программы и компоненты** выберите **Microsoft SQL Server 2012**.  
  
3.  В мастере удаления выберите экземпляр, который включает функцию экземпляра [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **RS**.  
  
     ![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")  
  
4.  После выбора экземпляра выберите компонент [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     ![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")  
  
5.  Завершите работу мастера.  
  
## <a name="see-also"></a>См. также статью  
 [Удаление существующего экземпляра SQL Server (программа установки)](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41; ](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)   
 [Установка или удаление надстройки Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
