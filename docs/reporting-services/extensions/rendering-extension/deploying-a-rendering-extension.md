---
title: "Развертывание модуля подготовки отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
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
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 3fbab7c48a0d522519a9e7ada9cf9c8cb1d40c7b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="deploying-a-rendering-extension"></a>Развертывание модуля подготовки отчетов
  После написания и компиляции вашей [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] отчета модуль подготовки отчетов в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] библиотеки, необходимо сделать его видимым, сервер отчетов и конструктора отчетов. Это можно сделать, скопировав модуль в подходящий каталог и добавив записи в подходящие файлы конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="configuration-file-rendering-extension-element"></a>Настройка элемента модуля подготовки отчетов в файле  
 После компиляции модуля подготовки отчетов в формат .DLL в файл rsreportserver.config добавляется запись. По умолчанию находится в папке %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<Имя_экземпляра > \Reporting Services\ReportServer. Родительский элемент является \<отрисовки >. В элементе Render находятся элементы Extension для каждого модуля подготовки отчетов. Элемент **Extension** содержит два атрибута — Name и Type.  
  
 В следующей таблице описываются атрибуты элемента **Extension** для модулей подготовки отчетов.  
  
|Attribute|Description|  
|---------------|-----------------|  
|**Имя**|Уникальное имя элемента Extension. Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extensions** файла конфигурации. Если присутствует повторяющееся имя, сервер отчетов возвращает ошибку.|  
|**Тип**|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|**Visible**|Значение **false** показывает, что модуль подготовки отчетов не должен быть видим в пользовательских интерфейсах. Если атрибут не указан, по умолчанию используется значение **true**.|  
|**LogAllExecutionRequests**|Значение **false** показывает, что запись регистрируется только для первого выполнения отчета в сеансе. Если атрибут не указан, по умолчанию используется значение **true**.<br /><br /> Например, этот параметр показывает, нужно ли регистрировать запись только для первой страницы, которая готовится к просмотру в составе отчета (значение **false**), или нужно создавать запись для каждой страницы, которая готовится к просмотру в составе отчета (значение **true**).|  
  
 Дополнительные сведения см. в разделе [Файл конфигурации RsReportServer.config](../../../reporting-services/report-server/rsreportserver-config-configuration-file.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Развертывание модуля на сервере отчетов  
 Сервер отчетов использует модули подготовки отчетов для экспорта отчетов в других форматах. Сборка модуля подготовки отчетов развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов rsreportserver.config.  
  
### <a name="to-deploy-the-assembly"></a>Развертывание сборки  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль подготовки отчетов. Расположение по умолчанию каталог Bin сервера отчетов располагается в %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<Имя_экземпляра > \Reporting Services\ReportServer\Bin.  
  
2.  Скопировав файл сборки, откройте файл rsreportserver.config. Файл rsreportserver.config также расположен в каталоге bin сервера отчетов. Необходимо создать запись в файле конфигурации для файла сборки модуля. Можно открыть файл с [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором.  
  
     Дополнительные сведения см. в разделе [Файл конфигурации RsReportServer.config](../../../reporting-services/report-server/rsreportserver-config-configuration-file.md).  
  
3.  В файле Rsreportserver.config найдите элемент **Render** . Запись для созданного модуля должна находиться в следующем разделе файла:  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля подготовки отчетов. В новую запись должен входить элемент, для которого заданы параметры **Name** и **Type**, например  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     Значение атрибута **Name** является уникальным именем модуля подготовки отчетов. Значение для **тип** является список с разделителями запятыми, который содержит запись для полного имени пространства имен вашей <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> реализацию, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули подготовки отчетов являются видимыми. Чтобы скрыть модуль в таких пользовательских интерфейсах, как диспетчер отчетов, добавьте атрибут **Visible** к элементу **Extension** и задайте для него значение **false**.  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных типов экспорта отчета.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Рекомендации по обеспечению безопасности для модулей](../../../reporting-services/extensions/security-considerations-for-extensions.md)  
  
  
