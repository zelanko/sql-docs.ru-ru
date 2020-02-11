---
title: Развертывание модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b95fbb99affb91743d5b922f748cae5554736f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164414"
---
# <a name="deploying-a-delivery-extension"></a>Развертывание модуля доставки
  Сведения о конфигурации модулей доставки предоставляются в виде XML-файлов конфигурации. XML-файл соответствует схеме XML, определенной для модулей доставки. Модули доставки предоставляют инфраструктуру для настройки и изменения файла конфигурации.  
  
 В случае замены или обновления модуля доставки все подписки, с которыми он связан, остаются действительными.  
  
 После написания [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и компиляции модуля доставки в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] библиотеку необходимо скопировать расширение в соответствующий каталог и добавить запись в соответствующий [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] файл конфигурации, чтобы сервер отчетов мог его разместить.  
  
## <a name="configuration-file-extension-element"></a>Элемент Extension в файле конфигурации  
 Модули доставки, развернутые на сервере отчетов, необходимо указывать в файле конфигурации как элементы `Extension`. Файлом конфигурации для сервера отчетов является RSReportServer.config.  
  
 В приведенной ниже таблице описаны атрибуты для элемента `Extension` модулей доставки.  
  
|attribute|Description|  
|---------------|-----------------|  
|`Name`|Уникальное имя модуля (например, «Электронная почта сервера отчетов» для модуля доставки по электронной почте или «Общие папки сервера отчетов» для модуля доставки в общие папки). Длина атрибута `Name` не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент `Extension` файла конфигурации. Если присутствует повторяющееся имя, сервер отчетов возвращает ошибку.|  
|`Type`|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|`Visible`|Значение `false` показывает, что модуль доставки не должен быть видимым в пользовательских интерфейсах. Если атрибут не указан, по умолчанию используется значение `true`.|  
  
 Дополнительные сведения о файле RSReportServer.config см. в разделе [Файлы конфигурации служб Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Развертывание модуля на сервере отчетов  
 С помощью модулей доставки сервер отчетов обрабатывает и доставляет уведомления или отчеты. Сборка модуля доставки развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Развертывание сборки модуля доставки на сервере отчетов  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль доставки. По умолчанию каталог bin сервера отчетов находится в папке%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<Имя_экземпляра> \reporting Services\ReportServer\bin.  
  
    > [!IMPORTANT]  
    >  При попытке перезаписать существующую сборку модуля доставки необходимо сначала остановить службу сервера отчетов, а затем скопировать обновленную сборку. После окончания копирования сборки перезапустите службу.  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer. config находится в папке%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> \reporting Services\ReportServer Directory. Необходимо создать запись в файле конфигурации для файла сборки модуля доставки. Файл конфигурации можно открыть с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким, как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент `Delivery`. Запись для созданного модуля доставки должна находиться в следующем разделе файла:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля доставки. В новую запись должен входить элемент `Extension` со значениями параметров `Name` и `Type`. Запись может выглядеть, например следующим образом:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Значение атрибута `Name` является уникальным именем модуля доставки. Значением атрибута `Type` является список с разделителями-запятыми, который содержит запись для полного пространства имен класса, в котором реализован интерфейс <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули доставки являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как диспетчер отчетов, добавьте атрибут `Visible` к элементу `Extension` и задайте для него значение `false`.  
  
5.  Наконец, добавьте для пользовательской сборки группу кода, которая предоставляет модулю доставки разрешение `FullTrust`. Это можно сделать, добавив группу кода в файл rssrvpolicy. config, расположенный по умолчанию в%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<Имя_экземпляра> \reporting Services\ReportServer. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL-членство — это лишь одно из множества условий членства, которые можно выбрать для модуля доставки. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssRS](../../../includes/ssrs.md)]см. в разделе [Безопасная разработка (службы Reporting Services)](../secure-development/secure-development-reporting-services.md).  
  
## <a name="deploying-the-extension-to-report-manager"></a>Развертывание модуля в диспетчере отчетов  
 Если модуль доставки реализует интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, то этот модуль можно использовать со страницей «Подписка диспетчера отчетов». Чтобы сделать доступным пользовательский интерфейс подписки, необходимо выполнить развертывание модуля в диспетчере отчетов.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>Развертывание сборки модуля доставки в диспетчере отчетов  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin диспетчера отчетов. Расположением диспетчер отчетов каталога bin по умолчанию является%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<Имя_экземпляра> \reporting сервицес\репортманажер\бин.  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer. config находится в папке%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<InstanceName> \reporting Services\ReportServer Directory. Необходимо создать запись в файле конфигурации для файла сборки модуля доставки. Файл конфигурации можно открыть с помощью среды Visual Studio .NET или воспользоваться простым текстовым редактором (таким как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент `DeliveryUI`. Запись для созданного модуля доставки должна находиться в следующем разделе файла:  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля доставки. В новую запись должен входить элемент `Extension` со значениями параметров `Name` и `Type`. Запись может выглядеть, например, следующим образом:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     Значение атрибута `Name` является уникальным именем модуля доставки. Значением атрибута `Type` является список с разделителями-запятыми, который содержит запись для полного пространства имен класса, в котором реализован интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, за которым следует имя сборки (не включая расширение DLL для файла).  
  
    > [!IMPORTANT]  
    >  Значение атрибута `Name` должно быть идентичным соответствующим записям в файле конфигурации сервера отчетов и диспетчера отчетов. Если они отличаются друг от друга, то конфигурация сервера будет недопустимой.  
  
     Наконец, добавьте для пользовательской сборки группу кода, которая предоставляет модулю доставки разрешение `FullTrust`. Это можно сделать, добавив группу кода в файл RSmgrpolicy. config, расположенный по умолчанию в папке C:\Program Files\Microsoft SQL Server \ MSRS10_50. \<Имя_экземпляра> \reporting Services\ReportManager. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL-членство — это лишь одно из множества условий членства, которые можно выбрать для модуля доставки. Дополнительные сведения об обеспечении безопасности доступа к [!INCLUDE[ssRS](../../../includes/ssrs.md)]коду в см. в разделе [безопасность разработки &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль доставки на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных модулей доставки для подписки. Дополнительные сведения о диспетчер отчетов и подписках см. в разделе [подписки и доставка &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
