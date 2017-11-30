---
title: "Журнал приложений Windows | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
caps.latest.revision: "32"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2f34c31f34b79a5e2f40cc88cbf57c35ce582558
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="windows-application-log"></a>Журнал приложений Windows
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] записывают сообщения о событиях в журнал приложений Windows. Эти сообщения в журнале приложений можно использовать для определения событий, вызванных приложениями сервера отчетов, запущенными в локальной системе.  
  
## <a name="viewing-report-server-events"></a>Просмотр событий сервера отчетов  
 Программа просмотра событий позволяет просматривать данный журнал и фильтровать содержащиеся в нем сообщения. Дополнительные сведения о сообщениях о событиях см. в разделе [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md). Дополнительные сведения о журнале приложений Windows и программе просмотра событий см. в документации по продуктам Windows.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляют три источника событий:  
  
-   сервер отчетов (служба Windows сервера отчетов);  
  
-   Диспетчер отчетов  
  
-   обработчик планирования и доставки  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не позволяет выключить запись событий сервера отчетов в журнал приложений или управлять тем, какие события записывать. Схема, описывающая запись событий сервера отчетов, фиксирована. Ее нельзя расширить для поддержки определенных пользователем событий.  
  
 Следующая таблица описывает типы событий, записываемых сервером отчетов в журнал событий приложений.  
  
|Тип события|Description|  
|----------------|-----------------|  
|Сведения|Событие, описывающее успешные операции (например, запуск службы сервера отчетов).|  
|Предупреждение|Событие, означающее потенциальную проблему (например, нехватка места на диске).|  
|Ошибка|Событие, описывающее существенную проблему (например, сбой при запуске службы).|  
|Аудит успехов|Событие безопасности, регистрируемое при успешном входе в систему.|  
|Аудит ошибок|Событие, регистрируемое при неудачной попытке входа в систему.|  
  
## <a name="see-also"></a>См. также  
 [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
