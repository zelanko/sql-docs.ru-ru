---
title: Доступ к поставщику WMI для служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efbe03a4aab65f792b352eeb5b6c5130c4c32335
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783208"
---
# <a name="access-the-reporting-services-wmi-provider"></a>Доступ к поставщику WMI для служб Reporting Services
  Поставщик WMI служб Reporting Services отображает два класса WMI для администрирования экземпляров серверов отчетов, работающих в собственном режиме, путем создания сценариев:  
  
> [!IMPORTANT]  
>  Начиная с выпуска [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , поставщик WMI поддерживается только для серверов отчетов, работающих в собственном режиме. Серверы отчетов служб в режиме интеграции с SharePoint могут управляться со страниц центра администрирования SharePoint и с помощью скриптов PowerShell.  
  
|Класс|Пространство имен|Описание|  
|-----------|---------------|-----------------|  
|MSReportServer_Instance|Рут\микрософт\склсервер\репортсервер\ RS_ *\<енкодединстанценаме >* \v11|Основные сведения, необходимые клиенту для подключения к установленному серверу отчетов.|  
|MSReportServer_ConfigurationSetting|Рут\микрософт\склсервер\репортсервер\ RS_ *\<енкодединстанценаме >* \v11\Admin|Представляет установочные параметры и параметры времени выполнения для экземпляра сервера отчетов. Эти параметры хранятся в файле конфигурации для сервера отчетов.<br /><br /> **\*\* Важно. \*\*** Этот класс доступен только для пользователей с правами администратора.|  
  
 Экземпляр каждого из перечисленных выше классов создается для каждого экземпляра сервера отчетов. Вы можете использовать любые средства Microsoft или сторонних производителей для получения доступа к объектам WMI, которые отображаются сервером отчетов, включая программные интерфейсы WMI, отображаемые самой платформой .NET Framework. В этом разделе рассматривается процедура получения доступа и использования экземпляров классов WMI с помощью команды PowerShell [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a>Определение имени экземпляра в строке пространства имен  
 Имя экземпляра в пути к пространству имен для классов WMI служб Reporting Services представляет собой кодировку имен экземпляра, которая указывается вами при установке именованных экземпляров служб Reporting Services. Конкретно в именах экземплярах кодируются специальные символы. Например, подчеркивающая линия (_) кодируется как _5f, поэтому имя экземпляра My_Instance в пути к пространству имен WMI будет закодировано как My_5fInstance.  
  
 Для просмотра списка закодированных имен экземпляров вашего сервера отчетов в пути к пространству имен WMI используйте следующую команду PowerShell:  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a>Получение доступа к классам WMI Server с использованием PowerShell  
 Для получения доступа к классам WMI выполните следующую команду:  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 Например, для получения доступа к классу MSReportServer_ConfigurationSetting на экземпляре сервера отчетов по умолчанию узла myrshost, выполните следующую команду: Для успешного выполнения данной команды необходимо, чтобы экземпляр сервера отчетов по умолчанию был установлен на узле myrshost.  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 Синтаксис данной команды выводит все имена и значения свойств класса. Обратите внимание, что несмотря на то, что вы получаете доступ к классу в пространстве имени экземпляра сервера отчетов по умолчанию (RS_MSSQLSERVER), возвращаются все экземпляры класса MSReportServer_ConfigurationSetting. Например, если узел myrshost установлен с экземпляром сервера отчетов по умолчанию, а именованный экземпляр сервера отчетов назван SHAREPOINT, то после выполнения данной команды будут возвращены два объекта WMI и выведены имена и значения свойств для обоих экземпляров серверов отчетов.  
  
 Для возвращения определенного экземпляра класса при возвращении нескольких экземпляров, используйте параметр -Filter для фильтрации результатов на основании свойств с уникальными значениями, как, например, InstanceName. Например, чтобы вернуть только объект WMI для экземпляра сервера отчетов по умолчанию, используйте следующую команду:  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a>Запрос доступных методов и свойств  
 Для просмотра доступных методов и свойств в одном из классов WMI служб Reporting Services примените результаты из команды Get-WmiObject в команду Get-Member. Пример:  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 Документацию по свойствам и методам классов WMI Reporting Services см. в разделе...  
  
## <a name="use-a-wmi-method-or-property"></a>Использование метода или свойства WMI  
 Вы можете использовать доступные методы и свойства при наличии объектов WMI для классов служб Reporting Services. Например, при наличии именованного экземпляра сервера отчетов в режиме интеграции с SharePoint с названием SHAREPOINT можно использовать следующую последовательность команд для получения URL-адреса для сайта центра администрирования SharePoint:  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a>См. также статью
 [Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS)](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
