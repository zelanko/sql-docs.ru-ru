---
title: "Отчет программы командной строки сервера (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eb04937fc5c68bf2efb82ece9914c56409b7f325
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-server-command-prompt-utilities-ssrs"></a>Программы командной строки сервера отчетов (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включает несколько служебных программ командной строки, которые можно использовать для администрирования сервера отчетов. Эти программы автоматически устанавливаются при установке сервера отчетов.  
  
|Название|Командный файл|Поддерживаемый режим развертывания|Description|  
|----------|------------------|-------------------------------|-----------------|  
|Программа RSS|rs.exe|Собственный режим и режим интеграции с SharePoint. В выпуске [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] появилась поддержка режима с SharePoint.|Программа [rs](../../reporting-services/tools/rs-exe-utility-ssrs.md) является сервером скриптов, который можно применять для выполнения операций, выраженных в форме скриптов. Это средство используется для запуска [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] сценариев, предназначенных для копирования данных между базами данных сервера отчетов, публикации отчетов, создание элементов на сервере отчетов в базе данных и многое другое. Использование скриптов для администрирования сервера описывается в разделе [Написание скриптов для задач развертывания и администрирования](../../reporting-services/tools/script-deployment-and-administrative-tasks.md).|  
|Командлеты PowerShell||Только режим интеграции с SharePoint|Список командлетов Powershell см. в статье [Командлеты PowerShell для служб Reporting Services в режиме SharePoint](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|  
|rsconfig, программа|rsconfig.exe|Только собственный режим|Программа [rsconfig](../../reporting-services/tools/rsconfig-utility-ssrs.md) служит для настройки и управления соединением сервера отчетов с базой данных сервера отчетов. Кроме того, с ее помощью можно указать учетную запись пользователя, которую следует использовать для автоматической обработки отчетов. Дополнительные сведения см. в разделе [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md). Дополнительные сведения о конфигурации подключения см. в статье [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Программа rskeymgmt|rskeymgmt.exe|Только собственный режим|Программа [rskeymgmt](../../reporting-services/tools/rskeymgmt-utility-ssrs.md) представляет собой средство управления ключами шифрования. Ее можно использовать для создания резервной копии, применения, повторного создания и удаления симметричных ключей. Кроме того, она позволяет подключить экземпляр сервера отчетов к общей базе данных сервера отчетов. Программу Rskeymgmt можно использовать при восстановлении базы данных. Существующую базу данных можно повторно использовать на вновь установленном экземпляре, применив резервную копию симметричного ключа. Если ключи восстановить невозможно, программа rskeymgmt позволяет удалить больше не используемое зашифрованное содержимое. Хранению конфиденциальных данных и управлению ключами посвящены разделы [Хранение зашифрованных данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) и [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
  
> [!NOTE]  
>  Если предпочтительным является средство с графическим пользовательским интерфейсом, то вместо программ **rsconfig** и **rskeymgmt**можно использовать диспетчер конфигурации служб Reporting Services.  
  
## <a name="see-also"></a>См. также  
 [Службы Reporting Services Configuration Manager &#40; Основной режим &#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Средства служб отчетов](../../reporting-services/tools/reporting-services-tools.md)   
 [Отчеты служб отчетов сервера &#40; Основной режим &#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  
