---
title: Доступ к поставщику WMI для служб Reporting Services | Документы Майкрософт
ms.date: 11/02/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f793de9e36968021155387ce0f926899f81f753d
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50027783"
---
# <a name="access-the-reporting-services-wmi-provider"></a>Доступ к поставщику WMI для служб Reporting Services
  Поставщик WMI служб Reporting Services отображает два класса WMI для администрирования экземпляров серверов отчетов, работающих в собственном режиме, путем создания сценариев:  
  
> [!IMPORTANT]  
>  Начиная с выпуска [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , поставщик WMI поддерживается только для серверов отчетов, работающих в собственном режиме. Серверы отчетов служб в режиме интеграции с SharePoint могут управляться со страниц центра администрирования SharePoint и с помощью скриптов PowerShell.  
  
|Class|Пространство имен|Описание|  
|-----------|---------------|-----------------|  
|MSReportServer_Instance|root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v13|Основные сведения, необходимые клиенту для подключения к установленному серверу отчетов.|  
|MSReportServer_ConfigurationSetting|root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v13\Admin|Представляет установочные параметры и параметры времени выполнения для экземпляра сервера отчетов. Эти параметры хранятся в файле конфигурации для сервера отчетов.<br /><br /> **\*\* Важно. \*\*** Этот класс доступен только для пользователей с правами администратора.|  
  
 Экземпляр каждого из перечисленных выше классов создается для каждого экземпляра сервера отчетов. Вы можете использовать любые средства Microsoft или сторонних производителей для получения доступа к объектам WMI, которые отображаются сервером отчетов, включая программные интерфейсы WMI, отображаемые самой платформой .NET Framework. В этом разделе рассматривается процедура получения доступа и использования экземпляров классов WMI с помощью команды PowerShell [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a>Определение имени экземпляра в строке пространства имен  
 Имя экземпляра в пути к пространству имен для классов WMI служб Reporting Services представляет собой кодировку имен экземпляра, которая указывается вами при установке именованных экземпляров служб Reporting Services. Конкретно в именах экземплярах кодируются специальные символы. Например, подчёркивающая линия (_) кодируется как «_5f», поэтому имя экземпляра «My_Instance» в пути к пространству имен WMI будет закодировано как «My_5fInstance».  
  
 Для просмотра списка закодированных имен экземпляров вашего сервера отчетов в пути к пространству имен WMI используйте следующую команду PowerShell:  
  
```  
PS C:\windows\system32> Get-WmiObject –namespace root\Microsoft\SqlServer\ReportServer  –class __Namespace –ComputerName hostname | select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a>Получение доступа к классам WMI Server с использованием PowerShell  
 Для получения доступа к классам WMI выполните следующую команду:  
  
```  
PS C:\windows\system32> Get-WmiObject –namespace <namespacename> –class <classname> –ComputerName <hostname>  
```  
  
 Например, для получения доступа к классу MSReportServer_ConfigurationSetting на экземпляре сервера отчетов по умолчанию узла myrshost, выполните следующую команду: Для успешного выполнения данной команды необходимо, чтобы экземпляр сервера отчетов по умолчанию был установлен на узле myrshost.  
  
```  
PS C:\windows\system32> Get-WmiObject –namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 Синтаксис данной команды выводит все имена и значения свойств класса. Обратите внимание, что несмотря на то, что вы получаете доступ к классу в пространстве имени экземпляра сервера отчетов по умолчанию (RS_MSSQLSERVER), возвращаются все экземпляры класса MSReportServer_ConfigurationSetting. Например, если узел myrshost установлен с экземпляром сервера отчетов по умолчанию, а именованный экземпляр сервера отчетов назван SHAREPOINT, то после выполнения данной команды будут возвращены два объекта WMI и выведены имена и значения свойств для обоих экземпляров серверов отчетов.  
  
 Для возвращения определенного экземпляра класса при возвращении нескольких экземпляров, используйте параметр –Filter для фильтрации результатов на основании свойств с уникальными значениями, как например, InstanceName. Например, чтобы вернуть только объект WMI для экземпляра сервера отчетов по умолчанию, используйте следующую команду:  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v13\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost -filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a>Запрос доступных методов и свойств  
 Для просмотра доступных методов и свойств в одном из классов WMI служб Reporting Services примените результаты из команды Get-WmiObject в команду Get-Member. Пример:  
  
```  
PS C:\windows\system32> Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v13\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
## <a name="use-a-wmi-method-or-property"></a>Использование метода или свойства WMI  
 Вы можете использовать доступные методы и свойства при наличии объектов WMI для классов служб Reporting Services. Например, при наличии именованного экземпляра сервера отчетов в режиме интеграции с SharePoint с названием SHAREPOINT можно использовать следующую последовательность команд для получения URL-адреса для сайта центра администрирования SharePoint:  
  
```  
PS C:\windows\system32> $rsconfig = Get-WmiObject -namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v13\Admin" -class MSReportServer_ConfigurationSetting -ComputerName myrshost -filter "InstanceName='SHAREPOINT'"  
PS C:\windows\system32> $rsconfig.GetAdminSiteUrl()  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS)](../../reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
