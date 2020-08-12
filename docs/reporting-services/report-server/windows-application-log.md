---
title: Журнал приложений Windows | Документы Майкрософт
description: Узнайте, как просматривать сообщения о событиях в журнале приложений, которые создаются приложениями сервера отчетов, выполняющимися в локальной системе.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5466c8a3e839a6db9438fde3ca7ce295405f3f23
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547836"
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
  
|Тип события|Описание|  
|----------------|-----------------|  
|Сведения|Событие, описывающее успешные операции (например, запуск службы сервера отчетов).|  
|Предупреждение|Событие, означающее потенциальную проблему (например, нехватка места на диске).|  
|Error|Событие, описывающее существенную проблему (например, сбой при запуске службы).|  
|Аудит успехов|Событие безопасности, регистрируемое при успешном входе в систему.|  
|Аудит ошибок|Событие, регистрируемое при неудачной попытке входа в систему.|  
  
## <a name="see-also"></a>См. также:  
 [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
