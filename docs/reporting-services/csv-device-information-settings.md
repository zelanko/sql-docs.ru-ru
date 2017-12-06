---
title: "Настройки сведений об устройстве CSV | Документы Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
caps.latest.revision: "43"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: b3de919b1994f93f2ae63e94aeae98d6aaec6042
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="csv-device-information-settings"></a>Настройки сведений об устройстве CSV
  Настройки сведений об устройстве для модуля подготовки отчетов CSV позволяет изменять разделители и квалификаторы, а также указывать правила обработки разрывов строк. Также можно указать расширение файла, кодировку и определить включение строк заголовка в выходные данные. Поскольку разделителями, скорее всего, будут специальные символы, их следует кодировать в разделе CDATA, если параметры записываются в формате XML.  
  
 В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в текстовом формате.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**Кодировка**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework. Значение по умолчанию — **UTF-8**. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
|**ExcelMode**|Указывает, что выходные данные предназначены для Excel. Значение по умолчанию — **true**|  
|**FieldDelimiter**|Строка-разделитель, помещаемая в результат. По умолчанию используется запятая (,). Во время передачи значения этого параметра сведений об устройстве в URL-адрес его необходимо закодировать в формат URL-адреса. Например, символ табуляции в качестве разделителя должен иметь вид «%09».<br /><br /> Можно заменить разделитель полей по умолчанию на любой символ, в том числе символ табуляции. Для этого нужно изменить настройки сведений об устройстве в файле конфигурации. Например, чтобы использовать символ табуляции, измените параметр FieldDelimiter, указав значение \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter>.<br /><br /> В этом примере вместо [TAB] необходимо вставить символ табуляции, и в файле конфигурации появится пробел. Атрибут «xml:space» указывает средствам синтаксического анализа на необходимость сохранения пробельных символов.|  
|**FileExtension**|Расширение файла, помещаемое в результат. Значение по умолчанию — **.CSV**. Если указаны и параметр **FileExtension** , и параметр **Extension** , приоритет имеет параметр **FileExtension** .|  
|**NoHeader**|Показывает, исключается ли из выходных данных строка заголовка. Значение по умолчанию — **false**.|  
|**Квалификатор**|Строка-квалификатор, размещаемая вокруг результатов, содержащих разделитель полей или разделитель записей. Если результаты содержат квалификатор, квалификатор повторяется. Значение параметра **Qualifier** должно отличаться от значений параметров **FieldDelimiter** и **RecordDelimiter** . По умолчанию используется кавычка (").|  
|**RecordDelimiter**|Разделитель записей, помещаемый в конце каждой записи. Значением по умолчанию является \<cr>\<lf>.|  
|**SuppressLineBreaks**|Показывает, удаляются ли разрывы строк из данных, включаемых в выходной документ. Значение по умолчанию — **false**. Если задано значение **true**, то значением параметров **FieldDelimiter**, **RecordDelimiter**и **Qualifier** не может быть пробельный символ.|  
|**UseFormattedValues**|Показывает, помещаются ли форматированные строки в выходной CSV-документ. По умолчанию используется значение **true** , если параметр **ExcelMode** имеет значение **true**. В противном случае используется значение **false**.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
