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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 815eff4ba68cb35a5f38b98514cc5359347a42e3
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59937060"
---
# <a name="atom-device-information-settings"></a>Настройки сведений об устройстве ATOM
  Настройки сведений об устройстве для модуля подготовки отчетов Atom включают параметры отправки имени веб-канала Atom и используемую кодировку.  
  
 В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в документе службы данных.  
  
|Параметр|Значение|  
|-------------|-----------|  
|`DataFeed`|Если указано, веб-канал Atom подготавливается к просмотру в соответствии с именем канала, указанным в этой настройке. В противном случае производится подготовка к просмотру сервисного документа Atom для отчета. Уникальный автоматически сформированный идентификатор канала данных. Это значение используется для внутренних целей и не подлежит изменению.|  
|**Кодировка**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework. Значение по умолчанию — `UTF-8`. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
