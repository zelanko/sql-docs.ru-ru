---
title: "Использование доступа по URL-адрес в веб-приложении | Документы Microsoft"
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
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: b8d7aff6c9afdfa6e6fb322d028b9bccf5cbaaf5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="integrating-reporting-services-using-url-access---web-application"></a>Интеграция службы Reporting Services с использованием URL - веб-приложения
  Доступ по URL-адресам в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] специально разработан таким образом, чтобы можно было получить доступ по сети к отдельным отчетам. Этот тип доступа наилучшим образом подходит для интеграции средств просмотра и навигации по отчетам в пользовательских веб-приложениях. Использовать доступ по URL-адресам в веб-приложениях можно следующим образом.  
  
-   Задавать URL-адрес конкретного сервера отчетов на веб-сайте или портале.  
  
-   Применять метод формы POST и передавать параметры строки запроса по URL-адресу сервера отчетов с использованием полей формы.  
  
## <a name="url-access-through-direct-addressing"></a>Доступ к URL-адресу с помощью прямой адресации  
 Для доступа к серверу отчетов или элементу базы данных сервера отчетов по URL-адресу достаточно просто указать этот URL-адрес в веб-браузере или приложении. Можно также предусмотреть использование в URL-адресе параметров, которые могут повлиять на отображение отчета или ресурса, к которому осуществляется доступ. URL-адрес можно серверу отчетов через адресной строке веб-браузера или URL-адрес может быть источником **IFrame** , являющийся частью крупных веб-приложений или портала. Гиперссылки на отчеты можно размещать на различных веб-страницах портала, а также указывать, в каком именно фрейме страницы должен быть выведен отчет, или открывать в процессе доступа к отчету новое окно браузера.  
  
 В следующем примере гиперссылка указывает на фрейм с именем «main», который может отличаться от того фрейма, в котором находится гиперссылка. Гиперссылка может входить в состав веб-портала.  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 В предыдущем примере, параметры сведений об устройствах **LinkTarget** передается со значением «main» в строке запроса URL-адреса. Это позволяет гарантировать, что любые детализирующие ссылки в отчете также будут указывать на фрейм с именем «main».  
  
 Дополнительные сведения о настройки сведений об устройстве см. в разделе [передача настроек сведений об устройстве модулям подготовки отчетов](../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 Следует отметить, что многие серверы и браузеры ограничивают допустимое число символов в URL-адресе. В некоторых случаях длина адреса ограничена 256 символами. Чтобы обойти это ограничение, необходимо использовать запросы POST с передачей форм.  
  
> [!NOTE]  
>  Максимальная длина URL-адреса в обозревателе Internet Explorer составляет 2083 символа. Это ограничение относится к запросам по URL-адресу обоих типов, POST и GET. Тем не менее, на запрос POST не налагаются ограничения в связи с размером URL-адреса при передаче пар «имя/значение» в составе формы, поскольку они передаются в заголовке, а не в URL-адресе.  
  
## <a name="url-access-through-a-form-post-method"></a>Доступ по URL-адресу с помощью метода форм POST  
 Если пользователь запрашивает данные с сервера отчетов по URL-адресу, то в HTTP-запросе используется метод GET. Это аналогично передаче формы при условии METHOD="GET". На URL-запросы или операции передачи форм с параметром METHOD="GET" налагается ограничение, определяемое максимальным количеством символов, которые может обработать сервер или веб-браузер.  
  
 А при использовании запросов POST (с параметром METHOD="POST" и полями ввода) пары «имя/значение» передаются в заголовке, а не в URL-адресе. Поэтому пары «имя/значение» в строке запроса перестают быть частью URL-адреса, что позволяет передавать гораздо более длинные и сложные списки параметров.  
  
 При использовании прямого доступа пользователь может видеть URL-адрес, передаваемый на сервер отчетов, поэтому получает возможность изменить строку запроса или отметить для себя конкретный URL-запрос и параметры сервера отчетов, чтобы воспользоваться этими сведениями в дальнейшем.  
  
 В приведенном ниже образце HTML-кода показана форма, которая позволяет получить доступ к серверу отчетов с помощью конкретного URL-адреса и передать параметры строки запроса в составе полей ввода формы.  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 В предыдущем примере предусмотрено, что при нажатии пользователем кнопки на форме сервер отчетов возвращает отчет, подготовленный в формате HTML, который предназначен для просмотра в текущем фрейме. Сопоставимая строка доступа по URL-адресу может выглядеть примерно таким образом:  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a>См. также:  
 [Интеграция служб Reporting Services в приложения](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Интеграция служб Reporting Services с помощью URL-адресов](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Использование доступа по URL-адрес в приложении Windows](../../reporting-services/application-integration/integrating-reporting-services-using-url-access-windows-application.md)   
 [Доступ к URL-адрес &#40; Службы SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  

