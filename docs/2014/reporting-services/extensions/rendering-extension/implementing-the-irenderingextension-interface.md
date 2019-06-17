---
title: Реализация интерфейса IRenderingExtension | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68e965a523df8dadd03d77df8d3d522870f70a93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62987149"
---
# <a name="implementing-the-irenderingextension-interface"></a>Реализация интерфейса IRenderingExtension
  Модуль подготовки отчетов извлекает результаты из определения отчета, объединенного с реальными данными, и преобразует результирующие данные в формат, готовый к применению. Преобразование объединенных данных и форматирование осуществляется при помощи класса среды CLR, который реализует интерфейс <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>. Модель объекта преобразуется в формат вывода, который предназначен для средства просмотра, принтера или другого приложения вывода.  
  
 Интерфейс <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> имеет три метода, которые должны быть реализованы.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> подготавливает отчет к просмотру.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> подготавливает к просмотру определенный поток из отчета.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> возвращает дополнительные сведения, такие как значки, которые требуются отчету.  
  
 В следующих разделах данные методы обсуждаются более подробно.  
  
## <a name="render-method"></a>Метод Render  
 Метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> содержит аргументы, представляющие следующие объекты.  
  
-   *report* — отчет, который необходимо подготовить. Данный объект содержит свойства, данные и сведения о макете отчета. Report — это корневой узел дерева модели объектов отчета.  
  
-   Параметр *ServerParameters* одержит объект словаря строк с параметрами сервера отчетов (если такие существуют).  
  
-   Параметр *deviceInfo* содержит параметры устройства. Дополнительные сведения см. разделе [Передача параметров сведений об устройстве модулям подготовки отчетов](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   Параметр *clientCapabilities* содержит объект словаря <xref:System.Collections.Specialized.NameValueCollection> со сведениями о клиенте, для которого выполняется отрисовка.  
  
-   Параметр *RenderProperties* содержит сведения о результате отрисовки.  
  
-   Параметр *createAndRegisterStream* — это функция-делегат, которую можно вызвать для получения потока, в который будет осуществляться отрисовка.  
  
### <a name="deviceinfo-parameter"></a>Параметр deviceInfo  
 Параметр *deviceInfo* содержит параметры отрисовки, а не параметры отчета. Данные параметры передаются модулю подготовки отчетов. Значения *deviceInfo* преобразуются сервером отчетов в объект <xref:System.Collections.Specialized.NameValueCollection>. Элементы в параметре *deviceInfo* рассматриваются как значения без учета регистра. Если запрос на отрисовку поступил в результате доступа по URL-адресу, то параметры URL-адреса в формате `rc:key=value` преобразовываются в пары "ключ-значение" в объекте словаря *deviceInfo*. Код обнаружения браузера также поставляет следующие элементы в *clientCapabilities* словаря: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, тип и AcceptLanguage. Любая пара "имя-значение" в параметре *deviceInfo*, которую не удается распознать модулю подготовки отчетов, не учитывается. В следующем образце кода показывается образец метода <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>, возвращающего значки:  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>Метод RenderStream  
 Метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> подготавливает к просмотру определенный поток из отчета. Все потоки создаются при начальном вызове метода <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A>, однако изначально потоки не возвращаются клиенту. Данный метод используется для вторичных потоков (например, при подготовке отчетов в формате HTML) или дополнительных страниц многостраничного модуля подготовки отчетов (например, модуль подготовки изображений или модуль подготовки EMF).  
  
## <a name="getrenderingresource-method"></a>Метод GetRenderingResource  
 Метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> получает данные, не выполняя полную подготовку отчета. В некоторых случаях отчету необходимы данные, которые не требуют подготовки отчета. Например, если нужно получить значок, связанный с модулем подготовки отчетов, следует использовать параметр *deviceInfo*, содержащий единственный тег **\<Icon>** . В подобных случаях можно использовать метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля подготовки отчетов](implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](rendering-extensions-overview.md)  
  
  
