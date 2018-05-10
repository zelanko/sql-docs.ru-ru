---
title: Развертывание модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 99ada408d4f2a783d2a545d00f780763b7a27796
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deploying-a-delivery-extension"></a>Развертывание модуля доставки
  Сведения о конфигурации модулей доставки предоставляются в виде XML-файлов конфигурации. XML-файл соответствует схеме XML, определенной для модулей доставки. Модули доставки предоставляют инфраструктуру для настройки и изменения файла конфигурации.  
  
 В случае замены или обновления модуля доставки все подписки, с которыми он связан, остаются действительными.  
  
 После записи и компиляции модуля доставки службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в библиотеку [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] необходимо скопировать модуль в соответствующий каталог и добавить запись в соответствующий файл конфигурации [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], чтобы сервер отчетов мог найти этот модуль.  
  
## <a name="configuration-file-extension-element"></a>Элемент Extension в файле конфигурации  
 Модули доставки, развернутые на сервере отчетов, необходимо указывать в файле конфигурации как элементы **Extension**. Файлом конфигурации для сервера отчетов является RSReportServer.config.  
  
 В приведенной ниже таблице описаны атрибуты для элемента **Extension** модулей доставки.  
  
|attribute|Description|  
|---------------|-----------------|  
|**Название**|Уникальное имя модуля (например, «Электронная почта сервера отчетов» для модуля доставки по электронной почте или «Общие папки сервера отчетов» для модуля доставки в общие папки). Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extension** файла конфигурации. Если присутствует повторяющееся имя, сервер отчетов возвращает ошибку.|  
|**Тип**|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|**Visible**|Значение **false** показывает, что модуль доставки не должен быть видимым в пользовательских интерфейсах. Если атрибут не указан, по умолчанию используется значение **true**.|  
  
 Дополнительные сведения о файле RSReportServer.config см. в разделе [Файлы конфигурации служб Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Развертывание модуля на сервере отчетов  
 С помощью модулей доставки сервер отчетов обрабатывает и доставляет уведомления или отчеты. Сборка модуля доставки развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Развертывание сборки модуля доставки на сервере отчетов  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль доставки. По умолчанию каталог bin сервера отчетов располагается в %ProgramFiles%\Microsoft SQL Server\MSRS13.\<имя_экземпляра>\Reporting Services\ReportServer\Bin.  
  
    > [!IMPORTANT]  
    >  При попытке перезаписать существующую сборку модуля доставки необходимо сначала остановить службу сервера отчетов, а затем скопировать обновленную сборку. После окончания копирования сборки перезапустите службу.  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer.config находится в папке %ProgramFiles%\Microsoft SQL Server\MSRS13.\<имя_экземпляра>\Reporting Services\ReportServer. Необходимо создать запись в файле конфигурации для файла сборки модуля доставки. Файл конфигурации можно открыть с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент **Delivery**. Запись для созданного модуля доставки должна находиться в следующем разделе файла:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля доставки. В новую запись должен входить элемент **Extension** со значениями параметров **Name** и **Type**. Запись может выглядеть, например, следующим образом:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Значение атрибута **Name** является уникальным именем модуля доставки. Значением атрибута **Type** является список с разделителями-запятыми, который содержит запись для полного пространства имен класса, в котором реализован интерфейс <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, за которым следует имя сборки (не включая расширение DLL для файла). По умолчанию модули доставки являются видимыми. Чтобы скрыть модуль в таких пользовательских интерфейсах, как веб-портал, добавьте атрибут **Visible** к элементу **Extension** и задайте для него значение **false**.  
  
5.  Наконец, добавьте для пользовательской сборки группу кода, которая предоставляет разрешение **FullTrust** для модуля доставки. Это можно сделать, добавив группу кода в файл rssrvpolicy.config, который по умолчанию помещается в каталоге %ProgramFiles%\Microsoft SQL Server\MSRS13.\<имя_экземпляра>\Reporting Services\ReportServer. Пример группы кода показан ниже.  
  
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
  
     URL-членство — это лишь одно из множества условий членства, которые можно выбрать для модуля доставки. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssRS](../../../includes/ssrs-md.md)]см. в разделе [Безопасная разработка (службы Reporting Services)](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
   
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль доставки на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть веб-портал и убедиться, что модуль включен в список доступных модулей доставки для подписки. Дополнительные сведения веб-портале и подписках см. в разделе [Подписки и доставка (службы Reporting Services)](../../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
