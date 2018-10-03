---
title: Программы командной строки сервера отчетов (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fb8216c75ac29b01e527f5e0449330e51529b69e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191864"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a>Программы командной строки сервера отчетов (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предусмотрено несколько программ командной строки, с помощью которых можно администрировать сервер отчетов. Эти программы автоматически устанавливаются при установке сервера отчетов.  
  
|Имя|Командный файл|Поддерживаемый режим развертывания|Описание|  
|----------|------------------|-------------------------------|-----------------|  
|Программа RSS|rs.exe|Собственный режим и режим интеграции с SharePoint. В выпуске [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] появилась поддержка режима с SharePoint.|Программа [rs](rs-exe-utility-ssrs.md) является сервером скриптов, который можно применять для выполнения операций, выраженных в форме скриптов. Используйте эту программу для выполнения скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , предназначенных для копирования данных из одной базы данных сервера отчетов в другую, публикации отчетов, создания объектов в базе данных сервера отчетов и т. д. Использование скриптов для администрирования сервера описывается в разделе [Написание скриптов для задач развертывания и администрирования](script-deployment-and-administrative-tasks.md).|  
|Командлеты PowerShell||Только режим интеграции с SharePoint|Список командлетов powershell, см. в разделе [командлеты PowerShell для режима SharePoint служб Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|  
|rsconfig, программа|rsconfig.exe|Только собственный режим|[Rsconfig, программа](rsconfig-utility-ssrs.md) используется для настройки и управления подключения сервера отчетов к базе данных сервера отчетов. Кроме того, с ее помощью можно указать учетную запись пользователя, которую следует использовать для автоматической обработки отчетов. Дополнительные сведения см. в разделе [Сервер отчетов служб Reporting Services (основной режим)](../report-server/reporting-services-report-server-native-mode.md). Дополнительные сведения о конфигурации подключения см. в статье [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Программа rskeymgmt|rskeymgmt.exe|Только собственный режим|[Программа rskeymgmt](rskeymgmt-utility-ssrs.md) представляет собой средство управления ключами шифрования. Ее можно использовать для создания резервной копии, применения, повторного создания и удаления симметричных ключей. Кроме того, она позволяет подключить экземпляр сервера отчетов к общей базе данных сервера отчетов. Программу Rskeymgmt можно использовать при восстановлении базы данных. Существующую базу данных можно повторно использовать на вновь установленном экземпляре, применив резервную копию симметричного ключа. Если ключи восстановить невозможно, программа rskeymgmt позволяет удалить больше не используемое зашифрованное содержимое. Хранению конфиденциальных данных и управлению ключами посвящены разделы [Хранение зашифрованных данных сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) и [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
  
> [!NOTE]  
>  Если вы предпочитаете использовать инструмент, который содержит графический интерфейс пользователя, можно использовать диспетчер конфигурации служб Reporting Services, а не `rsconfig` и `rskeymgmt`.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Инструментальные средства служб Reporting Services](reporting-services-tools.md)   
 [Сервер отчетов служб Reporting Services (собственный режим)](../report-server/reporting-services-report-server-native-mode.md)  
  
  
