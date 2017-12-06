---
title: "Доступ к элементам сервера отчетов с использованием URL-адресов | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
caps.latest.revision: "40"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: bc3ca223d41188299db94acbd54ca80ca40de0f0
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="access-report-server-items-using-url-access"></a>Доступ к элементам сервера отчетов с использованием URL-адреса
  В этом разделе описываются методы доступа к элементам каталога различных типов в базе данных сервера отчетов или на сайте SharePoint с использованием строки *rs:Command*=*Value*. Указывать эту строку параметра не обязательно. Если она не указана, сервер отчетов оценивает тип элемента и выбирает подходящее значение параметра автоматически. Однако использование строки *rs:Command*=*Value* в URL-адресе улучшает производительность сервера отчетов.  
  
 Обратите внимание на синтаксис прокси `_vti_bin` в приведенных далее примерах. Дополнительные сведения об использовании этого синтаксиса см. в разделе [URL Access Parameter Reference](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Доступ к отчету  
 Чтобы открыть отчет в браузере, следует использовать параметр *rs:Command*=*Render* . Например:  
  
 - **Собственный** `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
 - **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  
  
## <a name="access-a-resource"></a>Доступ к ресурсу  
 Для доступа к ресурсу следует использовать параметр *rs:Command*=*GetResourceContents* . Если ресурс совместим с браузером (например, если это изображение), то он открывается в браузере. В противном случае будет предложено открыть или сохранить файл или ресурс на диск.  
  
 **Собственный** `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Доступ к источнику данных  
 Для доступа к источнику данных следует использовать параметр *rs:Command*=*GetDataSourceContents* . Если браузер поддерживает XML, то определение источника данных отображается при условии, что текущий пользователь прошел проверку подлинности и обладает разрешением **Read Contents** для источника данных. Например:  
  
 **Собственный** `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 XML-структура может иметь вид, аналогичный следующему примеру:  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 Строка соединения возвращается в зависимости от параметра **SecureConnectionLevel** для сервера отчетов. Дополнительные сведения о параметре **SecureConnectionLevel** см. в разделе [Using Secure Web Service Methods](../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Доступ к содержимому папки  
 Для доступа к содержимому папки следует использовать параметр *rs:Command*=*GetChildren* . Будет возвращена универсальная страница для переходов по папкам, содержащая вложенные папки, отчеты, источники данных и ресурсы запрошенной папки. Например:  
  
 **Собственный** `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Отображаемый пользовательский интерфейс аналогичен режиму просмотра каталогов, используемому на сервере [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS. Номер версии сервера отчетов, включая номер построения, также выводится под списком папок.  
  
## <a name="see-also"></a>См. также  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md) 
