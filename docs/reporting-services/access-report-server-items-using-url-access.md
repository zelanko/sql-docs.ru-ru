---
title: Доступ к элементам сервера отчетов с использованием URL-адресов | Документы Майкрософт
ms.date: 05/08/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 52222f154ccc8068c77b0925f246e738a66721cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581260"
---
# <a name="access-report-server-items-using-url-access"></a>Доступ к элементам сервера отчетов с использованием URL-адреса
  В этом разделе описываются методы доступа к элементам каталога различных типов в базе данных сервера отчетов или на сайте SharePoint с использованием строки *rs:Command*=*Value*. Указывать эту строку параметра не обязательно. Если она не указана, сервер отчетов оценивает тип элемента и выбирает подходящее значение параметра автоматически. Однако использование строки *rs:Command*=*Value* в URL-адресе улучшает производительность сервера отчетов.  
  
 Обратите внимание на синтаксис прокси `_vti_bin` в приведенных далее примерах. Дополнительные сведения об использовании этого синтаксиса см. в разделе [URL Access Parameter Reference](../reporting-services/url-access-parameter-reference.md).  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
## <a name="access-a-report"></a>Доступ к отчету  
 Чтобы открыть отчет в браузере, следует использовать параметр *rs:Command*=*Render* . Пример:  
  
 - **Собственный** `https://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

 - **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  

::: moniker-end
  
## <a name="access-a-resource"></a>Доступ к ресурсу  
 Для доступа к ресурсу следует использовать параметр *rs:Command*=*GetResourceContents* . Если ресурс совместим с браузером (например, если это изображение), то он открывается в браузере. В противном случае будет предложено открыть или сохранить файл или ресурс на диск.  
  
 **Собственный** `https://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  

::: moniker-end
  
## <a name="access-a-data-source"></a>Доступ к источнику данных  
 Для доступа к источнику данных следует использовать параметр *rs:Command*=*GetDataSourceContents* . Если браузер поддерживает XML, то определение источника данных отображается при условии, что текущий пользователь прошел проверку подлинности и обладает разрешением **Read Contents** для источника данных. Пример:  
  
 **Собственный** `https://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 XML-структура может иметь вид, аналогичный следующему примеру:  

::: moniker-end
  
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
 Для доступа к содержимому папки следует использовать параметр *rs:Command*=*GetChildren* . Будет возвращена универсальная страница для переходов по папкам, содержащая вложенные папки, отчеты, источники данных и ресурсы запрошенной папки. Пример:  
  
 **Собственный** `https://myrshost/reportserver?/Sales&rs:Command=GetChildren`  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 **SharePoint** `https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rs:Command=GetChildren`  

::: moniker-end
  
 Отображаемый пользовательский интерфейс аналогичен режиму просмотра каталогов, используемому на сервере [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS. Номер версии сервера отчетов, включая номер построения, также выводится под списком папок.  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md) 
