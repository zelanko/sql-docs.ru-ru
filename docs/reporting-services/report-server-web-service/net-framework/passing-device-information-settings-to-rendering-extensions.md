---
title: "Передача настроек сведений об устройстве для модулей подготовки отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: dfbc65590c676278c89ca2646dae0d347abcd3ee
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру
  В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]настройки сведений об устройстве используются для передачи параметров подготовки к просмотру модуля подготовки отчетов. Настройки веб-службы сервера отчетов передаются как XML-элемент **DeviceInfo** и обрабатываются сервером отчетов. Поскольку у настроек сведений об устройстве есть значения по умолчанию, в процессе подготовки к просмотру эти аргументы являются необязательными. Однако настройки сведений об устройстве можно использовать для настройки процесса подготовки к просмотру и переопределения значений по умолчанию, передаваемых сервером.  
  
 Настройки сведений об устройстве можно задавать различными способами. Для задания программным путем можно использовать метод Render. Если доступ к отчету осуществляется по URL-адресу, сведения об устройстве можно задать как параметры URL-адреса. Можно также редактировать настройки сведений об устройстве в файлах конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , чтобы задать глобальные значения параметров подготовки к просмотру. Дополнительные сведения об указании параметров подготовки к просмотру глобально см. в разделе [настройки параметров модуля подготовки отчетов в файле RSReportServer.Config](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Передача сведений об устройстве с помощью метода Render  
 To pass device information settings to a rendering extension, use the **M:Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.Warning[]@,System.String[]@)** method. Например, следующую строку XML могут передаваться <xref:ReportExecution2005.ReportExecutionService.Render%2A> метод для создания HTML-фрагмент при подготовке к просмотру в формате HTML.  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 При подготовке отчета в виде фрагмента HTML содержимое отчета находится в элементе TABLE, а элементы HTML и BODY не используются. Фрагмент HTML можно использовать для внедрения отчета в существующий HTML-документ. Дополнительные сведения о настройках сведений об устройстве для вывода в формате HTML см. в разделе [HTML Device Information Settings](../../../reporting-services/html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Передача сведений об устройстве с помощью доступа через URL-адрес  
 Настройки сведений об устройстве можно также передать с помощью доступа по URL-адресу. Настройки сведений об устройстве передаются как параметры URL-адреса. Чтобы создать готовый для просмотра отчет без панели инструментов средства просмотра HTML-страниц, можно передать серверу отчетов следующую строку доступа к URL-адресу:  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Дополнительные сведения см. в разделе [указать настройки сведений об устройстве в URL-АДРЕСЕ](../../../reporting-services/specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройки сведений об устройстве для подготовки к просмотру расширения &#40; Службы Reporting Services &#41;](../../../reporting-services/device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Настройка параметров модуля подготовки отчетов в RSReportServer.Config](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
