---
title: "Как: развертывание модуля обработки данных в конструкторе отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
caps.latest.revision: 41
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e5e309ee7092bdc64efa89fa27579e9e8944da14
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="deploying-a-data-processing-extension-to-report-designer"></a>Развертывание модуля обработки данных, конструктор отчетов
  Модули обработки данных используются в конструкторе отчетов для получения и обработки данных в процессе разработки отчетов. Сборка модуля обработки данных должна быть развернута в конструкторе отчетов как закрытая сборка. Необходимо также внести запись в файл конфигурации конструктора отчетов, RSReportDesigner.config.  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте конкретную сборку из промежуточной папки в каталог конструктора отчетов. По умолчанию каталог исполняемых файлов конструктора отчетов расположен в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
2.  После того, как будет скопирован файл сборки, откройте файл RSReportDesigner.config. Файл RSReportDesigner.config также находится в каталоге конструктора отчетов. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Можно открыть файл конфигурации с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или с простой текстовый редактор, например Блокнот.  
  
3.  Найдите в файле RSReportDesigner.config элемент **Data** . Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля обработки данных, включая **расширения** со значениями **имя**, **тип**, и **Visible** атрибуты. Эта запись должна иметь следующий вид:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     Значение для **имя** уникальное имя модуля обработки данных. Значение для **тип** является список с разделителями запятыми, который содержит запись для полного пространства имен, класса, который реализует <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> интерфейсы, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как конструктор отчетов, добавьте **Visible** атрибут **расширения** элемент и присвойте ему значение **false**.  
  
5.  Наконец, добавьте группу кода для пользовательской сборки, которая предоставляет **FullTrust** разрешение для модуля. С этой целью добавьте указанную группу кода в файл rspreviewpolicy.config, который по умолчанию находится в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies. Пример группы кода показан ниже.  
  
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
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения о безопасности доступа к коду в [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], в разделе [разработки безопасного &#40; Службы Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
## <a name="generic-query-designer"></a>Обычный конструктор запросов  
 В состав конструктора отчетов входит обычный конструктор запросов, который можно применять с пользовательскими модулями обработки данных. Конструктор состоит из двух панелей: панели запросов и панели результатов. С помощью универсального конструктора можно создавать запросы, не поддерживаемые при использовании графического интерфейса. В отличие от графического конструктора запросов, обычный конструктор запросов не проверяет синтаксис запроса и не изменяет структуру запроса.  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>Включение обычного конструктора запросов для пользовательского модуля  
  
-   Добавьте следующую запись в файл RSReportDesigner.config **конструктор** элемент, заменив **имя** атрибут с именем, которое указывалось в предыдущих элементах.  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Прежде чем выполнять проверку развертывания, необходимо закрыть все экземпляры среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] на локальном компьютере. После завершения всех текущих сеансов можно проверить, успешно ли развернут модуль обработки данных в конструкторе отчетов, создав с помощью среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] новый проект отчета. При создании набора данных для отчета модуль должен появиться в списке доступных типов источников данных.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
