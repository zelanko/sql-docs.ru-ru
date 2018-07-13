---
title: Развертывание модуля подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
caps.latest.revision: 43
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4847340ab6bb40a4a5c6e247a4b9f2e33034ca8e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181681"
---
# <a name="deploying-a-rendering-extension"></a>Развертывание модуля подготовки отчетов
  После того как модуль подготовки отчетов служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] был написан и скомпилирован в библиотеку [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], необходимо сделать его видимым для сервера отчетов и конструктора отчетов. Это можно сделать, скопировав модуль в подходящий каталог и добавив записи в подходящие файлы конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="configuration-file-rendering-extension-element"></a>Настройка элемента модуля подготовки отчетов в файле  
 После компиляции модуля подготовки отчетов в формат .DLL в файл rsreportserver.config добавляется запись. По умолчанию этот файл находится в папке %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<имя_экземпляра>\Reporting Services\ReportServer. Родительским элементом является \<Render>. В элементе Render находятся элементы Extension для каждого модуля подготовки отчетов. `Extension` Элемент содержит два атрибута, имя и тип.  
  
 В следующей таблице описаны атрибуты для `Extension` элемент для модулей подготовки отчетов:  
  
|attribute|Описание|  
|---------------|-----------------|  
|**Название**|Уникальное имя элемента Extension. Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extensions** файла конфигурации. Если присутствует повторяющееся имя, сервер отчетов возвращает ошибку.|  
|**Тип**|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|**Visible**|Значение `false` показывает, что модуль подготовки отчетов не должен быть видим в пользовательских интерфейсах. Если атрибут не включается, значение по умолчанию — `true`.|  
|**LogAllExecutionRequests**|Значение `false` показывает, что запись регистрируется только для первого выполнения отчета в сеансе. Если атрибут не включается, значение по умолчанию — `true`.<br /><br /> Например, этот параметр показывает, нужно ли регистрировать запись только для первой страницы, которая готовится к просмотру в составе отчета (значение `false`), или нужно создавать запись для каждой страницы, которая готовится к просмотру в составе отчета (значение `true`).|  
  
 Дополнительные сведения см. в статье [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Развертывание модуля на сервере отчетов  
 Сервер отчетов использует модули подготовки отчетов для экспорта отчетов в других форматах. Сборка модуля подготовки отчетов развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов rsreportserver.config.  
  
### <a name="to-deploy-the-assembly"></a>Развертывание сборки  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль подготовки отчетов. По умолчанию каталог bin сервера отчетов располагается в %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<имя_экземпляра>\Reporting Services\ReportServer\Bin.  
  
2.  Скопировав файл сборки, откройте файл rsreportserver.config. Файл rsreportserver.config также расположен в каталоге bin сервера отчетов. Необходимо создать запись в файле конфигурации для файла сборки модуля. Файл можно открыть с помощью среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором.  
  
     Дополнительные сведения см. в статье [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
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
  
     Значение атрибута **Name** является уникальным именем модуля подготовки отчетов. Значение атрибута **Type** — это список с разделителями-запятыми, который содержит запись пространства имен с полным именем реализации <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>, за которым следует имя сборки (без расширения DLL в имени файла). По умолчанию модули подготовки отчетов являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как диспетчер отчетов, добавьте **Visible** атрибут `Extension` элемент и присвойте ему значение `false`.  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных типов экспорта отчета.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля подготовки отчетов](implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Рекомендации по обеспечению безопасности для модулей](../security-considerations-for-extensions.md)  
  
  
