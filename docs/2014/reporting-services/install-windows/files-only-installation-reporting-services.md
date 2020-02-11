---
title: Установка в режиме "только файлы" (службы Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a854de693bce88fcba0de2f1c08e4b0fe296b512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108835"
---
# <a name="files-only-installation-reporting-services"></a>Установка в режиме «только файлы» (службы Reporting Services)
  *Установка только файлов* — это [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установка, при которой программа установки создает структуру папок для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] программных файлов, копирует файлы на диск, регистрирует службу сервера отчетов на локальном компьютере, настраивает учетную запись службы, предоставляет разрешения на файлы для учетной записи службы и регистрирует поставщик [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI.  
  
 Установка в режиме "только файлы" включает следующие компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] : службу сервера отчетов (которая включает веб-службу сервера отчетов, работающую в фоновом режиме, и диспетчер отчетов), построитель отчетов, средство настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и программы командной строки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe и rs.exe). Он не применяется к общим функциям, таким [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] как [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]или, которые должны быть указаны как отдельные элементы, если вы хотите установить их.  
  
 В отличие от других режимов, в режиме «только файлы» сервер отчетов не готов к запуску сразу же после окончания установки. Чтобы перевести сервер отчетов в режим "в сети" с помощью [диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md), необходима дополнительная настройка.  
  
## <a name="when-to-select-files-only-installation-mode"></a>Случаи, в которых следует выбирать режим «только файлы»  
 Установка в режиме «только файлы» должна производиться в следующих случаях.  
  
-   Необходимо подключить сервер отчетов к удаленной базе данных сервера отчетов.  
  
-   Сервер отчетов должен быть установлен как именованный экземпляр.  
  
-   Существуют требования к развертыванию, включающие специальную настройку или функциональность, и необходим полный контроль над процессом настройки сервера.  
  
-   Установка отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включающего службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="how-to-perform-a-files-only-installation"></a>Установка в режиме «только файлы»  
 Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]по умолчанию устанавливаются в режиме «только файлы».  
  
 Этот режим можно указать с помощью командной строки или выбрать в мастере установки. Пошаговые инструкции приводятся в следующих разделах.  
  
-   [Установите SQL Server 2014 с помощью мастера установки &#40;&#41;установки ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   [Установите SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
#### <a name="example-command-line-script"></a>Пример скрипта командной строки  
 Для ясности в примере приведен аргумент /RSINSTALLMODE="FilesOnlyMode". Однако, поскольку режим «только файлы» является режимом по умолчанию, с тем же результатом этот аргумент можно не указывать.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a>Мастер установки  
 При выборе служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на странице выбора компонентов программа установки открывает страницу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , позволяя указать режим установки. Чтобы выбрать установку в режиме "только файлы", на странице настройки службы **выберите параметр** Установить, но не настраивать сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Проверка установки Reporting Services](verify-a-reporting-services-installation.md)   
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;службы SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Reporting Services установки в режиме интеграции с SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md)   
 [Установка Reporting Services сервера отчетов в собственном режиме](install-reporting-services-native-mode-report-server.md)   
 [Инструментальные средства служб Reporting Services](../tools/reporting-services-tools.md)  
  
  
