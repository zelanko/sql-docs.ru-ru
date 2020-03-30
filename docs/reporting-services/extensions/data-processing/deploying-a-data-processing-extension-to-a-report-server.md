---
title: Практическое руководство. Развертывание модуля обработки данных на сервере отчетов | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b3f0b775b53244cd0a428bb4ce4023906d2f5119
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "63194116"
---
# <a name="deploying-a-data-processing-extension-to-a-report-server"></a>Развертывание модуля обработки данных на сервере отчетов
  Серверы отчетов используют модули обработки данных для получения и обработки данных в отчетах, готовых для просмотра. Сборка модуля обработки данных развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль обработки данных. По умолчанию каталог bin сервера отчетов располагается по пути %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*имя_экземпляра*>\Reporting Services\ReportServer\bin.  
  
    > [!NOTE]  
    >  Этот шаг предотвратит обновление до более нового экземпляра SQL Server. Дополнительные сведения см. в разделе [Upgrade and Migrate Reporting Services](../../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer.config расположен в каталоге ReportServer. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Файл конфигурации можно открыть с помощью среды Visual Studio или простого текстового редактора (такого как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент **Data** . Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для развертываемого модуля обработки данных. В новую запись должен входить элемент **Extension** со значениями параметров **Name** и **Type**. Запись может выглядеть следующим образом:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     По умолчанию **Name** — это уникальное имя модуля обработки данных. Значение параметра **Type** представляет собой список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, а затем имя сборки (без расширения DLL). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль в таких пользовательских интерфейсах, как диспетчер отчетов, добавьте атрибут **Visible** к элементу **Extension** и задайте для него значение **false**.  
  
5.  Добавьте для пользовательской сборки группу кода, которая предоставляет разрешение **FullTrust** вашему модулю. Это можно сделать, добавив группу кода в файл rssrvpolicy.config, который по умолчанию находится в каталоге %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*имя_экземпляра*>\Reporting Services\ReportServer. Пример группы кода показан ниже.  
  
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
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] см. в статье [Разработка безопасных приложений (службы Reporting Services)](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль обработки данных на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных источников данных. Дополнительные сведения о диспетчере отчетов и источниках данных см. в разделе [Создание, изменение и удаление общих источников данных (службы SSRS)](../../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
