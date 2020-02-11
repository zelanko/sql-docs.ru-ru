---
title: Настройки сведений об устройстве Word | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd145c5073003a8dc189e3ed9b1bbb25dc11d09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096932"
---
# <a name="word-device-information-settings"></a>Настройки сведений об устройстве Word
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Параметр|Значение|  
|-------------|-----------|  
|`AutoFit`|`False`. Для автоподбора установлено значение `false` в какой-либо таблице Word.<br /><br /> `True`. Для автоподбора установлено значение `true` во всех таблицах Word.<br /><br /> `Never`. Значения автоподбора не установлены ни в одной из таблиц Word, производится возврат к поведению по умолчанию для Word.<br /><br /> `Default`. Автоподбор установлен для таблиц, более узких, чем физическая область отрисовки (ширина физической страницы, включая поля) на логической странице.|  
|`ExpandToggles`|Указывает, должны ли все переключаемые элементы отображаться в полностью раскрытом состоянии. По умолчанию используется значение `false`.|  
|`FixedPageWidth`|Указывает, будет ли ширина страницы, записанная в DOC-файл, увеличиваться, чтобы уместилась самая широкая страница в тексте отчета. По умолчанию используется значение `false`.|  
|**омисиперлинкс**|Указывает, опускать ли действие гиперссылки для всех элементов, где оно установлено. По умолчанию используется значение `false`.|  
|`OmitDrillthroughs`|Указывает, опускать ли действие детализации для всех элементов, где оно установлено. По умолчанию используется значение `false`.|  
  
## <a name="see-also"></a>См. также:  
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
