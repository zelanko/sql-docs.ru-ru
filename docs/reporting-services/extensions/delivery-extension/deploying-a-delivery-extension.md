---
title: "Развертывание модуля доставки | Документы Microsoft"
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
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d072577828375a08c133bb1a68d93e652e5cf168
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="deploying-a-delivery-extension"></a>Развертывание модуля доставки
  Сведения о конфигурации модулей доставки предоставляются в виде XML-файлов конфигурации. XML-файл соответствует схеме XML, определенной для модулей доставки. Модули доставки предоставляют инфраструктуру для настройки и изменения файла конфигурации.  
  
 В случае замены или обновления модуля доставки все подписки, с которыми он связан, остаются действительными.  
  
 После был написан и скомпилирован вашей [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль доставки в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] библиотеки, необходимо скопировать модуль в подходящий каталог и добавить запись в соответствующую [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] файл конфигурации, чтобы сервер отчетов могли его найти.  
  
## <a name="configuration-file-extension-element"></a>Элемент Extension в файле конфигурации  
 Модули доставки, которые развертываются на сервере отчетов должны вводиться как **расширения** элементов в файле конфигурации. Файлом конфигурации для сервера отчетов является RSReportServer.config.  
  
 В следующей таблице описаны атрибуты для **расширения** элемент для модулей доставки.  
  
|Attribute|Description|  
|---------------|-----------------|  
|**Название**|Уникальное имя модуля (например, «Электронная почта сервера отчетов» для модуля доставки по электронной почте или «Общие папки сервера отчетов» для модуля доставки в общие папки). Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extension** файла конфигурации. Если присутствует повторяющееся имя, сервер отчетов возвращает ошибку.|  
|**Тип**|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|**Visible**|Значение **false** указывает, что модуль доставки не должны быть видимыми в пользовательском интерфейсе. Если атрибут не указан, по умолчанию используется значение **true**.|  
  
 Дополнительные сведения о файле RSReportServer.config см. в разделе [файлы конфигурации служб Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Развертывание модуля на сервере отчетов  
 С помощью модулей доставки сервер отчетов обрабатывает и доставляет уведомления или отчеты. Сборка модуля доставки развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Развертывание сборки модуля доставки на сервере отчетов  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль доставки. Расположение по умолчанию каталог bin сервера отчетов располагается в %ProgramFiles%\Microsoft SQL Server\MSRS13. \<Имя_экземпляра > \Reporting Services\ReportServer\bin.  
  
    > [!IMPORTANT]  
    >  При попытке перезаписать существующую сборку модуля доставки необходимо сначала остановить службу сервера отчетов, а затем скопировать обновленную сборку. После окончания копирования сборки перезапустите службу.  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer.config находится в %ProgramFiles%\Microsoft SQL Server\MSRS13. \<Имя_экземпляра > \Reporting Services\ReportServer каталога. Необходимо создать запись в файле конфигурации для файла сборки модуля доставки. Можно открыть файл конфигурации с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или простого текстового редактора, например «Блокнот».  
  
3.  Найдите **доставки** элемент в файле RSReportServer.config. Запись для созданного модуля доставки должна находиться в следующем разделе файла:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля доставки. Новую запись должен входить **расширения** со значениями **имя** и **тип**, может выглядеть следующим образом:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Значение для **имя** уникальное имя модуля доставки. Значение для **тип** является список с разделителями запятыми, который содержит запись для полного пространства имен, класса, который реализует <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> интерфейса, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули доставки являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как веб-портала, добавление **Visible** атрибут **расширения** элемент и присвойте ему значение **false**.  
  
5.  Наконец, добавьте группу кода для пользовательской сборки, которая предоставляет **FullTrust** разрешение для модуля доставки. Это сделать, добавив группу кода в файл rssrvpolicy.config, расположенный в %ProgramFiles%\Microsoft SQL Server\MSRS13 по умолчанию. \<Имя_экземпляра > \Reporting Services\ReportServer. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS13.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     URL-членство — это лишь одно из множества условий членства, которые можно выбрать для модуля доставки. Дополнительные сведения о безопасности доступа к коду в [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], см.[ Защита разработки &#40; Службы Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
   
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль доставки на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть веб-портала и убедитесь, что модуль включен в список доступных модулей доставки для подписки. Дополнительные сведения о веб-портала и подписках см. в разделе [&#40; подписки и доставки Службы Reporting Services &#41; ](../../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

