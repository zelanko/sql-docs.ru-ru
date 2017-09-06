---
title: "Реализация интерфейса IRenderingExtension | Документы Microsoft"
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
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 60eac755180faaba012c7fbd14001fcb66a37975
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

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
  
-   *Отчетов* , которую требуется отобразить. Данный объект содержит свойства, данные и сведения о макете отчета. Report — это корневой узел дерева модели объектов отчета.  
  
-   *ServerParameters* , содержит объект словаря строк с параметрами для сервера отчетов, если таковые имеются.  
  
-   *DeviceInfo* параметр, который содержит настройки устройств. Дополнительные сведения см. в разделе [передача настроек сведений об устройстве модулям подготовки отчетов](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   *ClientCapabilities* параметра, который содержит <xref:System.Collections.Specialized.NameValueCollection> объект словаря, который содержит сведения о клиенте, к которому выполняется подготовка к просмотру.  
  
-   *RenderProperties* , содержащий сведения о результате подготовки к просмотру.  
  
-   *CreateAndRegisterStream* является функция-делегат, вызываемый для получения потока для подготовки к просмотру в.  
  
### <a name="deviceinfo-parameter"></a>Параметр deviceInfo  
 *DeviceInfo* параметром подготовки к просмотру, не параметры отчета. Данные параметры передаются модулю подготовки отчетов. *DeviceInfo* значения преобразуются в <xref:System.Collections.Specialized.NameValueCollection> объекта на сервере отчетов. Элементы в *deviceInfo* рассматриваются как значения без учета регистра. Если запрос отрисовки пришел через URL-адрес доступ, параметры URL-адреса в форме `rc:key=value` преобразуются в пары "ключ значение" *deviceInfo* объект словаря. Код обнаружения браузера также поставляет следующие элементы в *clientCapabilities* словарь: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, тип и AcceptLanguage. Любое имя и значение в *deviceInfo* пропущен параметр, который не опознается модулем подготовки отчетов. В следующем образце кода показывается образец метода <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>, возвращающего значки:  
  
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
 Метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> получает данные, не выполняя полную подготовку отчета. В некоторых случаях отчету необходимы данные, которые не требуют подготовки отчета. Например, если нужно получить значок, связанный с модулем подготовки отчетов, используйте *deviceInfo* параметр, содержащий единственный тег  **\<значок >**. В подобных случаях можно использовать метод <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
  
  
