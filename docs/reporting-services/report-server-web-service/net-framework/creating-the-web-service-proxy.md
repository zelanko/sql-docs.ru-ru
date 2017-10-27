---
title: "Создание прокси веб-службы | Документы Microsoft"
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
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 1c39d81ec9a1d2cd24f01b9dccfed13e8560a770
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="creating-the-web-service-proxy"></a>Создание учетной записи-посредника веб-службы
  Клиент и веб-служба могут обмениваться данными с помощью сообщений SOAP, в который входные и выходные параметры инкапсулируются в формате XML. Класс-посредник сопоставляет параметры с XML-элементами, а затем отправляет сообщения SOAP по сети. Таким образом класс-посредник устраняет необходимость связываться с веб-службой на уровне SOAP и позволяет вызывать методы веб-службы в любой среде разработки, которая поддерживает протокол SOAP и прокси для веб-служб.  
  
 Существует два способа добавить класс-посредник в проект разработки с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: с помощью программы WSDL в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]и путем добавления веб-ссылки в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. В следующих подразделах эта тема описана более подробно.  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a>Добавление класса-посредника с помощью программы WSDL  
 Пакет SDK для [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] включает программу Wsdl.exe для работы с языком WSDL, которая позволяет создать прокси-класс веб-службы для использования в среде разработки [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Наиболее простой способ создания клиентского прокси на языках, поддерживающих веб-службы (в настоящее время C# и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) является использование средства WSDL.  
  
 **Чтобы добавить класс-посредник в проект с помощью Wsdl.exe**  
  
1.  Запустите программу Wsdl.exe из командной строки, чтобы создать класс-посредник, указав (по крайней мере) URL-адрес для веб-службы сервера отчетов.  
  
     Например, следующая инструкция командной строки указывает URL-адрес для конечной точки управления в веб-службе сервера отчетов:  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Программа WSDL принимает ряд аргументов командной строки для создания прокси-класса. В предыдущем примере для использования в классе-посреднике указывается язык C# и рекомендуемое пространство имен (чтобы предотвратить конфликт имен в случае использования нескольких конечных точек веб-службы), а затем создается файл кода C# с именем ReportingService2010.cs. Если в примере указать язык [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], будет создан прокси-файл с именем ReportingService2010.vb. Этот файл создается в каталоге, из которого запущена команда.  
  
2.  Скомпилируйте класс-посредник в файл сборки (с расширением DLL) и создайте в проекте ссылку на сборку или добавьте класс в качестве элемента проекта.  
  
    > [!NOTE]  
    >  Если класс-посредник добавляется в проект вручную, необходимо добавить ссылку на библиотеку System.Web.Services.dll. Если прокси-класс добавляется с помощью веб-ссылки в Visual Studio .NET, то ссылка создается автоматически. Дополнительные сведения см. в подразделе «Добавление класса-посредника с помощью веб-ссылки в Visual Studio» далее в этом разделе.  
  
     После добавления класса-посредника в качестве элемента проекта в обозревателе решений появляется соответствующий файл.  
  
3.  Чтобы вызвать службу программным образом, создайте экземпляр класса-посредника.  
  
     В следующем примере кода показан синтаксис для создания в проекте экземпляра класса-посредника <xref:ReportService2010.ReportingService2010>.  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 Дополнительные сведения о программе Wsdl.exe, включая полный синтаксис, см. в разделе «Программа WSDL» документации по пакету SDK для [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Полное описание прокси для веб-служб см. в разделе «Создание прокси для веб-служб с поддержкой XML» документации по пакету SDK для [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a>Добавление учетной записи-посредника с помощью веб-ссылки в Visual Studio  
 Веб-ссылка позволяет проекту использовать одну или несколько веб-служб. Среда [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] позволяет пользователям добавлять в проекты ссылки на веб-службы с помощью нескольких простых действий.  
  
 **Чтобы добавить веб-ссылку в проект**  
  
1.  В **обозревателе решений**, выберите проект, который будет использовать веб-службы.  
  
2.  На **проекта** меню, нажмите кнопку **Add Web Reference**.  
  
     **Add Web Reference** откроется диалоговое окно.  
  
3.  В **URL-адрес** введите полный путь отчета веб-службы сервера.  
  
     Упрощенный URL-адрес конечной точки выполнения отчета для веб-службы сервера отчетов может иметь следующий вид:  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     URL-адрес содержит домен, в котором развернута веб-служба сервера отчетов, имя папки, содержащей службу, и имя файла обнаружения для службы. Полное описание различных элементов URL-адрес см. в разделе [доступ к API-Интерфейс SOAP](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
     Описание методов и свойств, предоставляемых веб-службой, появляется слева в панели браузера.  
  
    > [!NOTE]  
    >  Дополнительные сведения об элементах, связанных с сервера веб-службы отчетов см. в разделе [методы веб-службы отчетов сервера](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md).  
  
4.  Убедитесь, что проект может использовать веб-службу сервера отчетов, а также в наличии необходимых разрешений для доступа к серверу отчетов.  
  
5.  В **имя веб-ссылки** введите имя, которое будет использоваться в коде для программного доступа к серверу веб-службы отчетов.  
  
6.  Выберите **добавить ссылку** кнопку, чтобы создать ссылку в приложении веб-службы.  
  
     Новая ссылка появится в **обозревателе решений** узле веб-ссылки для активного проекта имя, указанное в **имя веб-ссылки** поля.  
  
7.  В **обозревателе решений**, разверните папку веб-ссылок, чтобы отметить пространство имен для классов веб-ссылок, доступных для элементов в проекте.  
  
     После добавления веб-ссылки в проект, связанные с ним файлы отображаются в папки внутри папки веб-ссылок из **обозревателе решений**.  
  
 После добавления веб-ссылки используйте следующий код для создания экземпляра класса-посредника:  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 Можно также добавить **с помощью** (**импорта** в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) директив для службы веб-сервера отчетов ссылки. Если применить эту директиву, нет необходимости полностью уточнять типы пространства имен. Для этого добавьте в файл следующий код:  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a>См. также:  
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  

