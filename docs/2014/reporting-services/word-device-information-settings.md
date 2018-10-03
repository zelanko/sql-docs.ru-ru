---
title: Настройки сведений об устройстве Word | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7c6a084e7d2093d2f0bfc7d55ef7f16be5b83e1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126884"
---
# <a name="word-device-information-settings"></a>Настройки сведений об устройстве Word
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Настройка|Значение|  
|-------------|-----------|  
|`AutoFit`|`False`. Автоподбор установлен `false` значение во всех таблицах Word.<br /><br /> `True`. Для автоподбора установлено значение `true` во всех таблицах Word.<br /><br /> `Never`. Значения автоподбора не установлены ни в одной из таблиц Word, производится возврат к поведению по умолчанию для Word.<br /><br /> `Default`. Автоподбор установлен для таблиц, более узких, чем физическая область отрисовки (ширина физической страницы, включая поля) на логической странице.|  
|`ExpandToggles`|Указывает, должны ли все переключаемые элементы отображаться в полностью раскрытом состоянии. Значение по умолчанию — `false`.|  
|`FixedPageWidth`|Указывает, будет ли ширина страницы, записанная в DOC-файл, увеличиваться, чтобы уместилась самая широкая страница в тексте отчета. Значение по умолчанию — `false`.|  
|**OmitHyperlinks**|Указывает, опускать ли действие гиперссылки для всех элементов, где оно установлено. Значение по умолчанию — `false`|  
|`OmitDrillthroughs`|Указывает, опускать ли действие детализации для всех элементов, где оно установлено. Значение по умолчанию — `false`|  
  
## <a name="see-also"></a>См. также  
 [Передача настроек сведений об устройстве для модулей подготовки отчетов](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
