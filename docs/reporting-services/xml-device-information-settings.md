---
title: "Настройки сведений об устройстве XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML [службы Reporting Services], подготовка к просмотру"
  - "настройки сведений об устройстве [службы Reporting Services], подготовка к просмотру в формате PDF"
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Настройки сведений об устройстве XML
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате XML.  
  
|Настройка|Значения|Сведения|  
|-------------|------------|-------------|  
|**XSLT**|Путь в пространстве имен сервера отчетов к преобразованию XSLT, которое нужно применить к XML-файлу, например **/Transforms/myxslt**.|XSL-файл должен быть опубликованным ресурсом на сервере отчетов, а доступ к нему должен осуществляться по пути к элементу сервера отчетов. Значение этого параметра применяется после преобразования XSLT, указанного в отчете. Если применяется параметр **XSLT** , то параметр **OmitSchema** не учитывается.|  
|**MIMEType**|Тип многоцелевого расширения электронной почты в Интернете (MIME) для XML-файла.||  
|**UseFormattedValues**|**true**<br /><br /> **false**|Показывает, нужно ли выводить форматированное значение текстового поля при создании XML-данных.<br /><br /> Значение false показывает, что используется базовое значение текстового поля.|  
|**Indented**|**true**<br /><br /> **false**|Показывает, создается ли XML-код с отступами. По умолчанию используется значение **false** и создается сжатый XML-код без отступов.|  
|**OmitNamespace**|**true**<br /><br /> **false**|Указывает, опускать ли пространство имен по умолчанию в XML.<br /><br /> При значении true в XML не указывается пространство имен по умолчанию.<br /><br /> При значении false в XML указывается пространство имен по умолчанию со значением свойства DataSchema отчета. Свойство DataSchema по умолчанию является именем отчета.<br /><br /> Значение по умолчанию —**false**.|  
|**OmitSchema**|**true**<br /><br /> **false**|Показывает, нужно ли исключать расположение схемы из XML. Расположение атрибута SchemaLocation.<br /><br /> Значение по умолчанию для OmitSchema зависит от значения OmitNamespace:<br /><br /> Если OmitNamespace = False, то по умолчанию OmitSchema = **False**. Пользователь может переопределить значение по умолчанию, установив OmitSchema = True.<br /><br /> Если OmitNamespace = true, то OmitSchema будет функционировать как **True** независимо от значения, явно заданного для OmitShema.|  
|**Кодировка**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework.|Значение по умолчанию — **UTF-8**. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
|**FileExtension**|Расширение, используемое для создаваемого файла.||  
|**Схема**|Значение **true** показывает, что выводится схема XML. Значение по умолчанию — **false**.|Показывает, выводится ли в XML-код схема XSD или фактические XML-данные.|  
  
## См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  