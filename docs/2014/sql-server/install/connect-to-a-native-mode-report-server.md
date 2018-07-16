---
title: Соединиться с сервера отчетов в собственном режиме | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 27b2d2d93d83057fd2de408b4a0cb61dd1cd0771
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321784"
---
# <a name="connect-to-a-native-mode-report-server"></a>Соединение с сервером отчетов, работающим в собственном режиме
  Это диалоговое окно используется для подключения к локальному или удаленному [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] экземпляра сервера отчетов. Это средство нельзя использовать для подключения к более ранним версиям [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] серверов отчетов. Одновременно можно подключиться только к одному экземпляру.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager не используется для настройки и администрирования [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint. Для настройки сервера отчетов в режиме интеграции с SharePoint используется центр администрирования SharePoint и скрипты PowerShell. Дополнительные сведения см. в разделе [установить службы Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) устанавливается с уровнем прав доступа «highestAvailable». Это поведение предусмотрено намеренно. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует подключения к API-интерфейсам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI. Для некоторых средств [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI требуется более высокий уровень прав администратора.  
  
-   Чтобы соединиться с локальным экземпляром сервера отчетов, используйте значения по умолчанию и нажмите кнопку **Соединить**. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляет имя локального сервера и обнаруживает экземпляр по умолчанию. В большинстве случаев перед нажатием на кнопку **Соединить** изменять эти значения необязательно. В ситуациях, когда установлено более одного экземпляра, нужно выбирать тот, который будет использоваться.  
  
-   Чтобы соединиться с удаленным экземпляром сервера отчетов, введите имя сервера, нажмите кнопку **Найти**, выберите экземпляр и нажмите кнопку **Соединить**.  
  
 Чтобы открыть это диалоговое окно, запустите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Это диалоговое окно открывается немедленно после запуска программы. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Имя сервера**  
 Введите сетевое имя компьютера, на котором [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установлен. Вводите только имя компьютера, не включайте в него ни префикс, ни символы косой черты.  
  
 **Найти**  
 Найдите компьютер, указанный в **Имя сервера**.  
  
 **Экземпляр сервера отчетов**  
 Выберите, какие экземпляры подсоединять, если установлено несколько экземпляров сервера отчетов. Выбирать можно только допустимые экземпляры. Если вы используете более старых версиях [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, эти экземпляры не будут приводиться в списке.  
  
 **Подключить**  
 Соединитесь с указанным сервером и экземпляром.  
  
## <a name="see-also"></a>См. также  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
