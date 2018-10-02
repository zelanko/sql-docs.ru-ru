---
title: Практическое руководство. Развертывание модуля обработки данных в конструкторе отчетов | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a248250c1f5584a12bc40444d27c96ccc7e69416
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818692"
---
# <a name="deploying-a-data-processing-extension-to-report-designer"></a>Развертывание модуля обработки данных в конструкторе отчетов
  Модули обработки данных используются в конструкторе отчетов для получения и обработки данных в процессе разработки отчетов. Сборка модуля обработки данных должна быть развернута в конструкторе отчетов как закрытая сборка. Необходимо также внести запись в файл конфигурации конструктора отчетов, RSReportDesigner.config.  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте конкретную сборку из промежуточной папки в каталог конструктора отчетов. По умолчанию каталог исполняемых файлов конструктора отчетов расположен в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
2.  После того, как будет скопирован файл сборки, откройте файл RSReportDesigner.config. Файл RSReportDesigner.config также находится в каталоге конструктора отчетов. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Файл конфигурации можно открыть с помощью среды [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким как Блокнот).  
  
3.  Найдите в файле RSReportDesigner.config элемент **Data** . Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте для модуля обработки данных запись, которая включает элемент **Extension** со значениями атрибутов **Name**, **Type** и **Visible**. Эта запись должна иметь следующий вид:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     По умолчанию **Name** — это уникальное имя модуля обработки данных. Значение параметра **Type** представляет собой список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, а затем имя сборки (без расширения DLL). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль в таких пользовательских интерфейсах, как конструктор отчетов, добавьте атрибут **Visible** к элементу **Extension** и задайте для него значение **false**.  
  
5.  Наконец, добавьте для пользовательской сборки группу кода, которая предоставляет разрешение **FullTrust** для конкретного модуля. С этой целью добавьте указанную группу кода в файл rspreviewpolicy.config, который по умолчанию находится в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] см. в разделе [Безопасная разработка (службы Reporting Services)](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="generic-query-designer"></a>Обычный конструктор запросов  
 В состав конструктора отчетов входит обычный конструктор запросов, который можно применять с пользовательскими модулями обработки данных. Конструктор состоит из двух панелей: панели запросов и панели результатов. С помощью универсального конструктора можно создавать запросы, не поддерживаемые при использовании графического интерфейса. В отличие от графического конструктора запросов, обычный конструктор запросов не проверяет синтаксис запроса и не изменяет структуру запроса.  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>Включение обычного конструктора запросов для пользовательского модуля  
  
-   Добавьте приведенную ниже запись в файл конфигурации RSReportDesigner.config вслед за элементом **Designer**, заменив атрибут **Name** именем, которое было указано в предыдущих записях.  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Прежде чем выполнять проверку развертывания, необходимо закрыть все экземпляры среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] на локальном компьютере. После завершения всех текущих сеансов можно проверить, успешно ли развернут модуль обработки данных в конструкторе отчетов, создав с помощью среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] новый проект отчета. При создании набора данных для отчета модуль должен появиться в списке доступных типов источников данных.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
