---
title: Доступ к элементам сервера отчетов с использованием URL-адресов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb841d8014bd1a66d533c10c4740c016bb13e737
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66110098"
---
# <a name="access-report-server-items-using-url-access"></a>Доступ к элементам сервера отчетов с использованием URL-адреса
  В этом разделе описывается, как получить доступ к элементам каталога различных типов в базе данных сервера отчетов или на сайте SharePoint с помощью *RS: Command*=*value*.  
  
 Указывать эту строку параметра не обязательно. Если она не указана, сервер отчетов оценивает тип элемента и выбирает подходящее значение параметра автоматически. Однако использование строки значения *RS: Command*=** в URL-адресе повышает производительность сервера отчетов.  
  
 Обратите внимание на синтаксис прокси `_vti_bin` в приведенных далее примерах. Дополнительные сведения об использовании этого синтаксиса см. в разделе [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Доступ к отчету  
 Чтобы просмотреть отчет в браузере, используйте параметр *RS: команда*=*Render* . Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  
  
## <a name="access-a-resource"></a>Доступ к ресурсу  
 Чтобы получить доступ к ресурсу, используйте параметр *RS: Command*=*GetResourceContents* . Если ресурс совместим с браузером, например с изображением, он открывается в браузере. В противном случае будет предложено открыть или сохранить файл или ресурс на диск.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Доступ к источнику данных  
 Для доступа к источнику данных используйте параметр *RS: Command*=*GetDataSourceContents* . Если браузер поддерживает XML, то определение источника данных отображается при условии, что текущий пользователь прошел проверку подлинности и обладает разрешением `Read Contents` для источника данных. Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
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
  
 Строка соединения возвращается в зависимости от параметра **SecureConnectionLevel** для сервера отчетов. Дополнительные сведения о параметре **SecureConnectionLevel** см. в разделе [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Доступ к содержимому папки  
 Для доступа к содержимому папки используйте параметр *RS: Command*=*дочерние* . Будет возвращена универсальная страница для переходов по папкам, содержащая вложенные папки, отчеты, источники данных и ресурсы запрошенной папки. Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Отображаемый пользовательский интерфейс аналогичен режиму просмотра каталогов, используемому на сервере [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS. Номер версии сервера отчетов, включая номер построения, также выводится под списком папок.  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](url-access-parameter-reference.md)  
  
  
