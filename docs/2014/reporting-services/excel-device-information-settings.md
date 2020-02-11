---
title: Настройки сведений об устройстве Excel | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d71c83195c8f91984bbbce95bd00402928fdb36e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109211"
---
# <a name="excel-device-information-settings"></a>Настройки сведений об устройстве Excel
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Параметр|Значение|  
|-------------|-----------|  
|**OmitDocumentMap**|Показывает, нужно ли исключать схему документа из параметров отчетов, поддерживающих ее. По умолчанию используется значение `false`.|  
|**OmitFormulas**|Показывает, нужно ли исключать формулы из отчета, готового для просмотра. По умолчанию используется значение `false`.|  
|`SimplePageHeade`стандарт|Показывает, преобразуется ли верхний колонтитул страницы отчетов в верхний колонтитул Excel при подготовке к просмотру. Значение `false` показывает, что верхний колонтитул страницы при подготовке к просмотру преобразуется в первую строку листа. По умолчанию используется значение `false`.|  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
