---
title: Настройки сведений об устройстве XML | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e642034d445e52485874c71df110bff81b9c1aaf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096938"
---
# <a name="xml-device-information-settings"></a>Настройки сведений об устройстве XML
  В следующей таблице перечислены настройки сведений об устройстве для подготовки к просмотру в формате XML.  
  
|Параметр|Применение|  
|-------------|-----------|  
|`XSLT`|Путь в пространстве имен сервера отчетов к преобразованию XSLT, которое нужно применить к XML-файлу, например `/Transforms/myxslt`. XSL-файл должен быть опубликованным ресурсом на сервере отчетов, а доступ к нему должен осуществляться по пути к элементу сервера отчетов. Значение этого параметра применяется после преобразования XSLT, указанного в отчете. Если применяется параметр `XSLT`, то параметр `OmitSchema` не учитывается.|  
|**MIMEType**|Тип многоцелевого расширения электронной почты в Интернете (MIME) для XML-файла.|  
|**UseFormattedValues**|Показывает, нужно ли выводить форматированное значение текстового поля при создании XML-данных. Значение false показывает, что используется базовое значение текстового поля.|  
|**Indented**|Показывает, создается ли XML-код с отступами. По умолчанию используется значение `false` и создается сжатый XML-код без отступов.|  
|`OmitNamespace`|Указывает, опускать ли пространство имен по умолчанию в XML.<br /><br /> При значении true в XML не указывается пространство имен по умолчанию.<br /><br /> При значении false в XML указывается пространство имен по умолчанию со значением свойства DataSchema отчета. Свойство DataSchema по умолчанию является именем отчета.<br /><br /> Значение по умолчанию — `false`.|  
|`OmitSchema`|Показывает, нужно ли исключать расположение схемы из XML. Расположение атрибута SchemaLocation. Значение по умолчанию для OmitSchema зависит от значения OmitNamespace:<br /><br /> если OmitNamespace = False, то по умолчанию OmitSchema = `False`. Пользователь может переопределить значение по умолчанию, установив OmitSchema = True.<br /><br /> Если OmitNamespace = true, то OmitSchema будет функционировать как `True` независимо от значения явно заданного для OmitShema.|  
|**Кодирование**|Определенное комитетом по цифровым адресам в Интернете (IANA) название кодировки символов, поддерживаемой платформой .NET Framework. Значение по умолчанию — `UTF-8`. В качестве примеров других значений можно привести ASCII, UTF-7 и UTF-16.|  
|**FileExtension**|Расширение, используемое для создаваемого файла.|  
|**схема**|Показывает, выводится ли в XML-код схема XSD или фактические XML-данные. Значение `true` показывает, что выводится схема XML. Значение по умолчанию — `false`.|  
  
## <a name="see-also"></a>См. также  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Передача настроек сведений об устройстве в модули подготовки отчетов](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модуля подготовки отчетов в файле RSReportServer. config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
