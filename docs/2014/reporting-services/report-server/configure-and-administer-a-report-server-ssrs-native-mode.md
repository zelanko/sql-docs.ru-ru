---
title: Настройка и администрирование сервера отчетов (службы SSRS в собственном режиме) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e31465f0f1099536e262442db894e5d6bfd6d37e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104001"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a>Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)
  В этом разделе приводится сводка подходов, которые можно использовать для настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Он также включает список разделов, в которых объясняется, как настраивать конкретные компоненты, функции и возможности сервера. Для настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]можно.  
  
-   Используйте диспетчер конфигурации служб Reporting Services. Многие подразделы этого раздела содержат сведения о том, как настраивать конкретные возможности с помощью этого средства.  
  
-   Используйте среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , чтобы включить папку "Мои отчеты", включить журналы трассировки и установить значения по умолчанию для уровня сайта. Дополнительные сведения о настройках сайта см. в разделе [Сервер отчетов служб Reporting Services (основной режим)](reporting-services-report-server-native-mode.md) для среды Management Studio. Обратите внимание, что можно создать и запустить скрипт, который программно задает свойства сервера. Дополнительные сведения см. в статьях [Написание скриптов для задач развертывания и администрирования](../tools/script-deployment-and-administrative-tasks.md) и [Системные свойства сервера отчетов](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).  
  
-   Использовать диспетчер отчетов, чтобы предоставить разрешения на доступ к серверу отчетов. Разрешения предоставляются с помощью назначения ролей для каждой учетной записи пользователя или группы пользователей. Дополнительные сведения см. в статье [Роли и разрешения (службы Reporting Services)](../security/roles-and-permissions-reporting-services.md).  
  
-   Дополнительно можно изменить файлы конфигурации для изменения настроек приложений. Дополнительные сведения о каждом файле и рекомендации по их изменению см. в разделе [Reporting Services Configuration Files](reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Описывает способ определения URL-адресов, используемых для доступа к серверу отчетов и диспетчеру отчетов.  
  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Содержит рекомендации и описывает шаги по изменению учетной записи службы и пароля.  
  
 [Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Описывает, как создать базу данных сервера отчетов, необходимую для хранения метаданных и объектов сервера.  
  
 [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Описывает, как изменить строку, используемую сервером отчетов для подключения к базе данных сервера отчетов.  
  
 [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Описывает, как настроить сервер отчетов для поддержки рассылки отчетов по электронной почте.  
  
 [Настройка учетной записи автоматического выполнения (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Описывает, как настроить пользовательскую учетную запись для обработки отчетов в автоматическом режиме.  
  
## <a name="see-also"></a>См. также  
 [настроить доступ к построителю отчетов](configure-report-builder-access.md)   
 [Reporting Services Configuration Files](reporting-services-configuration-files.md)   
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Защита и обеспечение безопасности служб Reporting Services](../security/reporting-services-security-and-protection.md)   
 [Сервер отчетов служб Reporting Services (собственный режим)](reporting-services-report-server-native-mode.md)  
  
  
