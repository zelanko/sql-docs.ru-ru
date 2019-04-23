---
title: Журнал приложений Windows | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8557f8b838eeec837cef0966f173f94626518aa7
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59960280"
---
# <a name="windows-application-log"></a>Журнал приложений Windows
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] записывают сообщения о событиях в журнал приложений Windows. Эти сообщения в журнале приложений можно использовать для определения событий, вызванных приложениями сервера отчетов, запущенными в локальной системе.  
  
## <a name="viewing-report-server-events"></a>Просмотр событий сервера отчетов  
 Программа просмотра событий позволяет просматривать данный журнал и фильтровать содержащиеся в нем сообщения. Дополнительные сведения о сообщениях о событиях см. в разделе [Справочник по ошибкам и событиям (службы Reporting Services)](../troubleshooting/errors-and-events-reference-reporting-services.md). Дополнительные сведения о журнале приложений Windows и программе просмотра событий см. в документации по продуктам Windows.  
  
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
|Ошибка|Событие, описывающее существенную проблему (например, сбой при запуске службы).|  
|Аудит успехов|Событие безопасности, регистрируемое при успешном входе в систему.|  
|Аудит ошибок|Событие, регистрируемое при неудачной попытке входа в систему.|  
  
## <a name="see-also"></a>См. также  
 [Файлы и источники журналов служб Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
