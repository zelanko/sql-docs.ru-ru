---
title: Настройки сведений об устройстве ATOM | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a424f7af44f6272f0d511a68b1e29d89b90d3372
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108504"
---
# <a name="atom-device-information-settings"></a>Настройки сведений об устройстве ATOM
  Настройки сведений об устройстве для модуля подготовки отчетов Atom включают параметры отправки имени веб-канала Atom и используемую кодировку.  
  
 В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в документе службы данных.  
  
|Настройка|Значение|  
|-------------|-----------|  
|`DataFeed`|Если указано, веб-канал Atom подготавливается к просмотру в соответствии с именем канала, указанным в этой настройке. В противном случае производится подготовка к просмотру сервисного документа Atom для отчета. Уникальный автоматически сформированный идентификатор канала данных. Это значение используется для внутренних целей и не подлежит изменению.|  
|**Кодировка**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework. Значение по умолчанию — `UTF-8`. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве для модулей подготовки отчетов](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
