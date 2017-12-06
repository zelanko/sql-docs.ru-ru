---
title: "Журнал приложений Windows | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: ee91a42ddd7abc16d39afdf5a6f6d3259a8f2fb5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
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
  
  
