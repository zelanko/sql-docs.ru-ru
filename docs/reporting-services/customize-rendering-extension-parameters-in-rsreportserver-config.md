---
title: "Настройка параметров модуля в файле RSReportServer.Config подготовки отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 009b40c83d662b40b3215f701a2eb490ebc4fed1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a>Настройка параметров модулей подготовки отчетов в RSReportServer.Config
  В файле конфигурации RSReportServer можно указать параметры модулей подготовки отчетов, чтобы изменить заданный по умолчанию способ подготовки к просмотру отчетов, запускаемых на сервере отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Изменять параметры модуля подготовки отчетов можно для достижения следующих целей.  
  
-   Изменение имени модуля подготовки отчетов в списке «Экспорт» панели инструментов отчета (например, чтобы заменить «Веб-архив» на «MHTML») или отображение этого имени на другом языке.  
  
-   Создание нескольких экземпляров одного модуля подготовки отчетов для обеспечения различных вариантов представления отчета (например, варианты модуля подготовки изображений портретной и альбомной ориентации).  
  
-   Изменение параметров по умолчанию модуля подготовки отчетов на другие значения (например, в модуле подготовки изображений в качестве формата вывода по умолчанию используется TIFF; параметры можно изменить таким образом, чтобы вместо этого использовался формат EMF).  
  
 Изменение параметров модуля подготовки отчетов влияет только на операции подготовки к просмотру на сервере отчетов. Невозможно изменить настройки модуля подготовки отчетов, используемые для предварительного просмотра отчета в конструкторе отчетов.  
  
 Указание параметров модуля подготовки отчетов в файлах конфигурации влияет на все модули подготовки к просмотру. Настройки в файлах конфигурации используются вместо значений по умолчанию всегда, когда применяется определенный модуль подготовки к просмотру. Если требуется задать параметры модуля подготовки отчетов для определенного отчета или операции подготовки к просмотру, следует указать сведения об устройстве программно с помощью метода <xref:ReportExecution2005.ReportExecutionService.Render%2A> или указав настройки сведений об устройстве в URL-адресе отчета. Дополнительные сведения об указании настроек сведений об устройстве для операции подготовки к просмотру, а также полный список этих настроек см. в разделе [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a>Поиск и изменение файла RSReportServer.config  
 Параметры конфигурации форматов вывода для отчета указывается в виде параметров модуля подготовки отчетов в файле конфигурации RSReportServer.config. Чтобы указать в файлах конфигурации параметры модуля подготовки отчетов, необходимо знать, как определить XML-структуры, задающие параметры подготовки к просмотру. Существует две XML-структуры, которые можно изменять.  
  
-   Элемент **OverrideNames** задает отображаемые имя и язык модуля подготовки отчетов.  
  
-   XML-структура **DeviceInfo** определяет настройки сведений об устройстве, используемых модулем подготовки отчетов. Большинство параметров модуля подготовки отчетов определены как настройки сведений об устройстве.  
  
 Для изменения этого файла можно использовать текстовый редактор. Файл RSReportServer.config находится в папке \Reporting Services\Report Server\Bin. Дополнительные сведения об изменении файлов конфигурации см. в разделе [изменения файла конфигурации служб Reporting Services &#40; Файл RSreportserver.config &#41; ](../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="changing-the-display-name"></a>Изменение отображаемого имени  
 Отображаемое имя модуля подготовки отчетов указывается в списке «Экспорт» панели инструментов отчета. Среди примеров отображаемых имен по умолчанию есть веб-архив, TIFF-файл и файл Acrobat (PDF-файл). Отображаемое имя по умолчанию можно заменить произвольным значением, указав в файлах конфигурации элемент **OverrideNames** . Кроме того, если пользователь определяет два экземпляра одного модуля подготовки отчетов, элемент **OverrideNames** можно использовать, чтобы различать эти экземпляры в списке «Экспорт».  
  
 Поскольку отображаемые имена локализованы, при замене отображаемого имени по умолчанию пользовательским значением следует установить атрибут **Language** . Иначе любое указанное имя не будет обрабатываться. Указанное значение языка должно быть допустимым для компьютера, на котором выполняется сервер отчетов. Например, если сервер отчетов выполняется под управлением французской операционной системы, в качестве значения атрибута следует указать «fr-FR».  
  
 В следующем примере показано, как задать пользовательское имя на сервере отчетов английской версии.  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a>Изменение настроек сведений об устройстве  
 Чтобы изменить настройки сведений об устройстве, используемые по умолчанию уже развернутым на сервере отчетов модулем подготовки отчетов, следует ввести в файлы конфигурации XML-структуру **DeviceInfo** . Для каждого модуля подготовки к просмотру существуют уникальные для него настройки сведений об устройстве. Полный список настроек сведений об устройстве см. в разделе [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 В следующем примере показано, как выглядит структура и синтаксис XML-кода, изменяющего значения по умолчанию для модуля подготовки изображений:  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a>Настройка нескольких записей для модуля подготовки к просмотру  
 Чтобы поддерживать возможность работы с различными представлениями отчета, можно создать несколько экземпляров одного модуля подготовки отчетов. Сочетание значений параметров может быть разным для каждого из определенных экземпляров. Определяя новые экземпляры существующего модуля подготовки отчетов, необходимо выполнить следующие действия.  
  
-   Указать уникальное имя для модуля.  
  
     Каждый экземпляр должен иметь уникальное значение атрибута **Name** . В следующем примере для того, чтобы экземпляры можно было различить, им присвоены имена «IMAGE (EMF Landscape)» и «IMAGE (EMF Portrait)».  
  
     Соблюдайте осторожность при изменении имени уже развернутого модуля подготовки отчетов. Разработчики, указывающие модули подготовки отчетов программно, используют имена модулей, чтобы обозначить, какой экземпляр нужен для определенной операции подготовки к просмотру. Если на сервере отчетов работают пользовательские приложения служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , убедитесь, что разработчику известно об изменениях, вносимых в существующие имена модулей, или о добавлении нового имени.  
  
-   Укажите такое уникальное отображаемое имя, чтобы пользователи могли понять, каковы различия между любыми форматами вывода.  
  
     При настройке нескольких версий одного модуля задайте каждой из них уникальное имя, указав значение для **OverrideNames**. В противном случае в списке возможных режимов экспорта на панели инструментов отчета все версии этого модуля будут отображаться под одним и тем же именем.  
  
 В следующем образце показано, как добиться, чтобы используемый по умолчанию модуль подготовки к просмотру изображений (осуществляющий вывод в формате TIFF) выводил отчет в формате EMF в портретной ориентации наряду со вторым экземпляром, выводящим отчеты в формате EMF в альбомной ориентации. Обратите внимание, что каждое имя модуля уникально. Помните, что при тестировании этого образца следует выбирать отчеты, не содержащие таких интерактивных возможностей, как скрытие/отображение параметров, матрицы или ссылки на детализированные отчеты (в модуле подготовки к просмотру изображений интерактивные возможности не работают):  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a>См. также  
 [Файл конфигурации RsReportServer.config](../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Файл конфигурации RSReportDesigner](../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Настройки сведений об устройстве CSV](../reporting-services/csv-device-information-settings.md)   
 [Настройки сведений об устройстве Excel](../reporting-services/excel-device-information-settings.md)   
 [Настройки сведений об устройстве HTML](../reporting-services/html-device-information-settings.md)   
 [Изображение настройки сведений об устройстве](../reporting-services/image-device-information-settings.md)   
 [Настройки сведений об устройстве MHTML](../reporting-services/mhtml-device-information-settings.md)   
 [Настройки сведений об устройстве PDF](../reporting-services/pdf-device-information-settings.md)   
 [Настройки сведений об устройстве XML](../reporting-services/xml-device-information-settings.md)  
  
  
