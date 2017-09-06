---
title: "Как: развертывание модуля обработки данных на сервере отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: a60c685ebdfd9d549e100cf5b5eda0ab056c1c46
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="deploying-a-data-processing-extension-to-a-report-server"></a>Развертывание модуля обработки данных на сервере отчетов
  Серверы отчетов используют модули обработки данных для получения и обработки данных в отчетах, готовых для просмотра. Сборка модуля обработки данных развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль обработки данных. Расположение по умолчанию каталог bin сервера отчетов располагается в %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \< *Имя экземпляра*> \Reporting Services\ReportServer\bin.  
  
    > [!NOTE]  
    >  Этот шаг предотвратит обновление до более нового экземпляра SQL Server. Дополнительные сведения см. в разделе [Upgrade and Migrate Reporting Services](../../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer.config расположен в каталоге ReportServer. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Файл конфигурации можно открыть в Visual Studio или простого текстового редактора, например «Блокнот».  
  
3.  Найдите в файле RSReportServer.config элемент **Data** . Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для развертываемого модуля обработки данных. Новую запись должен входить **расширения** со значениями **имя** и **типа** и может выглядеть следующим образом:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     Значение для **имя** уникальное имя модуля обработки данных. Значение для **тип** является список с разделителями запятыми, который содержит запись для полного пространства имен, класса, который реализует <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> интерфейсы, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль в таких пользовательских интерфейсах, как диспетчер отчетов, добавьте атрибут **Visible** к элементу **Extension** и задайте для него значение **false**.  
  
5.  Добавьте группу кода для пользовательской сборки, которая предоставляет **FullTrust** разрешение для модуля. Это можно сделать, добавив группу кода в файл rssrvpolicy.config, расположенный в %ProgramFiles%\Microsoft SQL Server по умолчанию\\< MSRS10_50.\< *Имя экземпляра*> \Reporting Services\ReportServer. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения о безопасности доступа к коду в [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], в разделе [разработки безопасного &#40; Службы Reporting Services &#41; ](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль обработки данных на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных источников данных. Дополнительные сведения о службах Reporting Services и источниках данных см. в статье [Создание, изменение и удаление общих источников данных (службы SSRS)](../../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
