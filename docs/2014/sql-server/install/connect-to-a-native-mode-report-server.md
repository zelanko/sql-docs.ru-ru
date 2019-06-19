---
title: Соединиться с сервера отчетов в собственном режиме | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6fd7ff677fdbbfa91b616fd6a561d3eb48c2de57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096062"
---
# <a name="connect-to-a-native-mode-report-server"></a>Соединение с сервером отчетов, работающим в собственном режиме
  Используйте это диалоговое окно для подключения к локальному или удаленному экземпляру сервера отчетов служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или более поздней версии. Это средство нельзя использовать для подключения к более ранним версиям сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Одновременно можно подключиться только к одному экземпляру.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
> [!NOTE]  
>  Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не используется для настройки и администрирования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Для настройки сервера отчетов в режиме интеграции с SharePoint используется центр администрирования SharePoint и скрипты PowerShell. Дополнительные сведения см. в статье [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) устанавливается с уровнем прав доступа «highestAvailable». Это поведение предусмотрено намеренно. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует подключения к API-интерфейсам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI. Для некоторых средств [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI требуется более высокий уровень прав администратора.  
  
-   Чтобы соединиться с локальным экземпляром сервера отчетов, используйте значения по умолчанию и нажмите кнопку **Соединить**. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляет имя локального сервера и обнаруживает экземпляр по умолчанию. В большинстве случаев перед нажатием на кнопку **Соединить** изменять эти значения необязательно. В ситуациях, когда установлено более одного экземпляра, нужно выбирать тот, который будет использоваться.  
  
-   Чтобы соединиться с удаленным экземпляром сервера отчетов, введите имя сервера, нажмите кнопку **Найти**, выберите экземпляр и нажмите кнопку **Соединить**.  
  
 Чтобы открыть это диалоговое окно, запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Это диалоговое окно открывается немедленно после запуска программы. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Имя сервера**  
 Введите сетевое имя компьютера, на котором установлены службы [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или более поздней версии. Вводите только имя компьютера, не включайте в него ни префикс, ни символы косой черты.  
  
 **найти**  
 Найдите компьютер, указанный в **Имя сервера**.  
  
 **Экземпляр сервера отчетов**  
 Выберите, какие экземпляры подсоединять, если установлено несколько экземпляров сервера отчетов. Выбирать можно только допустимые экземпляры. Если выполняются более ранние версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параллельно с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , эти экземпляры не будут приводиться в списках.  
  
 **Подключить**  
 Соединитесь с указанным сервером и экземпляром.  
  
## <a name="see-also"></a>См. также  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
