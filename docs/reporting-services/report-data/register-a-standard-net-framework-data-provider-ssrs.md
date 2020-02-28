---
title: Регистрация стандартного поставщика данных .NET Framework | Документация Майкрософт
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f9435584579e36e46d55aa6723e0ade60b6642b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081948"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a>Регистрация стандартного поставщика данных .NET Framework (службы SSRS)
  Чтобы набор данных отчета служб [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] получал данные с помощью поставщика данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сторонней разработки, необходимо развернуть и зарегистрировать сборку поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] в двух местах: на клиенте, используемом для разработки отчета, и на сервере отчетов. На клиенте поставщик данных должен быть зарегистрирован в качестве типа источника данных и связан с конструктором запросов. После этого этот поставщик может быть выбран в качестве типа источника данных при создании набора данных для отчета. При этом откроется связанный конструктор запросов, помогающий создавать запросы для этого типа источников данных. На сервере отчетов поставщик данных необходимо зарегистрировать в качестве типа источника данных. После этого может производиться обработка опубликованных отчетов, которые в качестве источника данных используют этот поставщик.  
  
 Поставщикам данных сторонней разработки не обязательно обеспечивать все функции, реализуемые модулями обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md). Дополнительные сведения о расширении функций поставщика данных платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе [Реализация модуля обработки данных](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 Для установки и регистрации поставщиков данных необходимы учетные данные администратора.  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a>Регистрация поставщика данных .NET Framework на сервере отчетов  
 Для обработки опубликованных отчетов, использующих этот поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] на сервере отчетов, на нем необходимо установить сборку. Необходимо изменить два файла конфигурации. Регистрация поставщика данных производится в файле rsreportserver.config. Чтобы предоставить права доступа к коду сборки необходимо изменить файл rssrvpolicy.config.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a>Установка сборки поставщика данных на сервер отчетов  
  
1.  Перейдите в каталог bin по умолчанию сервера отчетов, на котором планируется использование поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . По умолчанию каталог bin сервера отчетов находится в папке *\<диск>* :\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.  
  
2.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов. Можно также загрузить сборку в глобальный кэш сборок (GAC). Дополнительные сведения см. в разделе [Работа со сборками и глобальным кэшем сборок](https://go.microsoft.com/fwlink/?linkid=63912) в документации по пакету SDK платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] на веб-узле MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a>Регистрация сборки поставщика данных на сервере отчетов  
  
1.  Создайте резервную копию файла RSReportServer.config в папке ReportServer, в которую вложен каталог bin.  
  
2.  Откройте RSReportServer.config. Файл конфигурации можно открыть с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким, как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент **Data** . Элемент для поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте элемент для поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
    |attribute|Описание|  
    |---------------|-----------------|  
    |**имя**;|Уникальное имя поставщика данных, например **MyNETDataProvider**. Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extension** файла конфигурации. Указываемое здесь значение выводится в раскрывающемся списке типов источников данных при создании нового источника данных.|  
    |**Тип**|Список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейс <xref:System.Data.IDbConnection> , а затем имя сборки поставщика [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (без расширения DLL).|  
  
     Например, для DLL-файла, развертываемого в каталоге bin сервера отчетов новый элемент может выглядеть следующим образом.  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     При загрузке сборки в глобальный кэш сборок необходимо указать свойства строгого имени. Пример:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a>Настройка групповой политики кода для поставщика данных .NET  
  
1.  Создайте резервную копию файла rssrvpolicy.config в папке ReportServer, в которую вложен каталог bin.  
  
2.  Откройте rssrvpolicy.config. Файл конфигурации можно открыть с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким, как Блокнот).  
  
3.  Найдите в файле rssrvpolicy.config элемент **CodeGroup** .  
  
4.  Добавьте группу кода для сборки поставщика данных, предоставляющую разрешение **FullTrust** , как показано ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 Членство URL — это лишь одно из множества условий членства, которые должны быть заданы для поставщика данных.  
  
### <a name="verifying-the-deployment-and-registration"></a>Проверка развертывания и регистрация  
 Успешность развертывания поставщика данных на сервере отчетов можно проверить по его наличию в списке доступных источников данных, открыв веб-портал. Дополнительные сведения о веб-портале и источниках данных см. в статье [Создание, изменение и удаление общих источников данных (службы SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a>Регистрация поставщика данных .NET Framework на клиенте конструктора отчетов  
 Для разработки отчетов, которые используют в качестве источника данных поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , необходимо установить сборку на клиентский компьютер, на котором запускается конструктор отчетов. Необходимо изменить два файла конфигурации. Измените файл RSReportDesigner.config для регистрации поставщика данных как источника данных и использования обычного конструктора запросов. Чтобы предоставить права доступа к коду сборки, измените файл RSPreviewPolicy.config.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a>Установка сборки поставщика данных на клиенте конструктора отчетов  
  
1.  Перейдите в каталог по умолчанию PrivateAssemblies на клиенте конструктора отчетов, на котором будет использоваться поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . По умолчанию каталог PrivateAssemblies расположен в папке *\<диск>* :\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
2.  Скопируйте сборку из промежуточной папки в каталог PrivateAssemblies клиента конструктора отчетов. Можно также загрузить сборку в глобальный кэш сборок (GAC). Дополнительные сведения см. в разделе [Работа со сборками и глобальным кэшем сборок](https://go.microsoft.com/fwlink/?linkid=63912) в документации по пакету SDK платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] на веб-узле MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a>Регистрация сборки поставщика данных на клиенте конструктора отчетов  
  
1.  Создайте резервную копию файла RSReportDesigner.config в каталоге PrivateAssemblies.  
  
2.  Откройте файл RSReportDesigner.config с помощью среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или простого текстового редактора (например, Блокнота).  
  
3.  Найдите в файле RSReportDesigner.config элемент **Data** . Элемент для поставщика данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте элемент для поставщика данных.  
  
    |attribute|Описание|  
    |---------------|-----------------|  
    |**имя**;|Уникальное имя поставщика данных, например **MyNETDataProvider**. Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extension** файла конфигурации. Указанное здесь значение отображается в раскрывающемся списке типов источников данных при создании нового источника данных.|  
    |**Тип**|Список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейс <xref:System.Data.IDbConnection> , а затем имя сборки поставщика [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (без расширения DLL).|  
  
     Например, для DLL-файла, развертываемого в каталоге PrivateAssemblies [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , новый элемент может выглядеть следующим образом.  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     Если сборка загружена в глобальный кэш сборок, необходимо задать свойства строгого имени. Пример:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  Найдите в файле RSReportDesigner.config элемент **Designer** . Элемент для поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  Добавьте в файл RSReportDesigner.config после элемента **Designer** следующий элемент. Атрибут **Name** необходимо заменить именем, которое указывалось в предыдущих элементах.  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a>Настройка групповой политики кода для поставщика данных .NET на клиенте конструктора отчетов  
  
1.  Создайте резервную копию файла RSPreviewPolicy.config в каталоге PrivateAssemblies.  
  
2.  Откройте файл RSPreviewPolicy.config с помощью среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или простого текстового редактора (например Блокнота).  
  
3.  Найдите в файле RSPreviewPolicy.config элемент **CodeGroup** .  
  
4.  Добавьте группу кода для сборки поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , предоставляющую разрешение **FullTrust** , как показано ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 Членство URL — это лишь одно из множества условий членства, которые должны быть заданы для поставщика данных.  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a>Проверка развертывания и регистрации на клиенте конструктора отчетов  
 Прежде чем выполнять проверку развертывания, необходимо закрыть все экземпляры среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] на локальном компьютере. После завершения всех текущих сеансов можно проверить успешность развертывания поставщика данных в конструкторе отчетов, создав с помощью среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]новый проект отчета. При создании набора данных для отчета поставщик данных должен появиться в списке доступных типов источников данных.  
  
## <a name="platform-considerations"></a>Замечания о платформе  
 На 64-разрядной (x64) платформе среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] выполняется в 32-разрядном режиме WOW. При разработке отчетов на платформе x64, для обеспечения их просмотра на клиенте конструктора отчетов необходимо установить 32-разрядную версию поставщика данных. Если отчет публикуется в той же системе, необходимо установить поставщики данных для архитектуры x64, чтобы просматривать отчеты на веб-портале.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] не поддерживается платформами на базе [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].  
  
 Модули обработки данных, установленные в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , должны быть скомпилированы для каждой из платформ и установлены в соответствующие каталоги. Если регистрируется пользовательский или стандартный поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , то он должен быть скомпилирован для целевой платформы и установлен в соответствующий каталог. При работе на 32-разрядной платформе поставщик данных должен быть скомпилирован для 32-разрядной платформы, а при работе на 64-разрядной платформе — для 64-разрядной платформы. 32-разрядный поставщик данных с 64-разрядными интерфейсами на 64-разрядной платформе использовать нельзя. Сведения о работоспособности на установленной платформе поставщика данных сторонней разработки см. в документации по этому программному обеспечению. Дополнительные сведения о поставщиках данных и поддержке платформ см. в разделе [Источники данных, поддерживаемые службами Reporting Services (службы SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Реализация модуля обработки данных](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Управление доступом для кода в службах Reporting Services](../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
