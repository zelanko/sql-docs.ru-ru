---
title: Доступ к элементам сервера отчетов с использованием URL-адрес | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a345cd609c4cfd79f9e93a2b63e71bbddde36ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233570"
---
# <a name="access-report-server-items-using-url-access"></a>Доступ к элементам сервера отчетов с помощью URL-адресов
  В этом разделе описываются методы доступа к элементам каталога различных типов в отчете данные сервера или на сайте SharePoint с помощью *rs: Command*=*значение*.  
  
 Необязательно указывать эту строку параметра. Если он пропущен, сервер отчетов оценивает тип элемента и автоматически выбирает подходящее значение параметра. Тем не менее, с помощью *rs: Command*=*значение* строку в URL-АДРЕСЕ улучшает производительность сервера отчетов.  
  
 Примечание `_vti_bin` синтаксис прокси, в приведенных ниже примерах. Дополнительные сведения об использовании этого синтаксиса см. в разделе [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Доступ к отчету  
 Чтобы просмотреть отчет в браузере, используйте *rs: Command*=*визуализации* параметра. Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Очень важно включить URL-адрес `_vti_bin` синтаксис прокси для отправки запроса с помощью центра администрирования SharePoint и [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] прокси-сервер HTTP. Прокси-сервер добавляет некоторый контекст HTTP-запроса, контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме SharePoint.  
  
## <a name="access-a-resource"></a>Доступ к ресурсу  
 Чтобы получить доступ к ресурсу, используйте *rs: Command*=*GetResourceContents* параметра. Если ресурс совместим с браузером, такие как изображения, он открывается в браузере. В противном случае вам предложено открыть или сохранить файл или ресурс на диск.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Доступ к источнику данных  
 Чтобы получить доступ к источнику данных, используйте *rs: Command*=*GetDataSourceContents* параметра. Если браузер поддерживает XML, то определение источника данных отображается в случае пользователь прошел проверку `Read Contents` разрешение в источнике данных. Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 Структура XML может выглядеть следующим образом:  
  
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
  
 Строка соединения возвращается в зависимости от **SecureConnectionLevel** Установка сервера отчетов. Дополнительные сведения о **SecureConnectionLevel** настройки, см. в разделе [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Доступ к содержимому папки  
 Чтобы получить доступ к содержимому папки, используйте *rs: Command*=*GetChildren* параметра. Возвращаемая страница универсального перемещение по папкам, содержащий ссылки на вложенные папки, отчеты, источники данных и ресурсы запрошенной папки. Пример:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Пользовательский интерфейс, вы увидите похож на режим просмотра каталогов [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS). Номер версии, включая номер сборки сервера отчетов, также отображается под списком папок.  
  
## <a name="see-also"></a>См. также  
 [URL-адресов &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL Access Parameter Reference](url-access-parameter-reference.md)  
  
  
