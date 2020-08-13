---
title: Задание языка для параметров отчета в URL-адресе | Документы Майкрософт
description: Узнайте, как задать язык для параметров отчета в URL-адресе с помощью параметра доступа по URL-адресу RS:ParameterLanguage.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5972235f37a8cc10968d68a614bab00f3ca9a556
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245711"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a>Задать язык для параметров отчета в URL-адресе
  Параметр *rs:ParameterLanguage* для доступа по URL-адресу устраняет проблему, когда для интерпретации таких региональных параметров отчета, как дата, время, валюта и числа, используется язык браузера. URL-адрес с указанным параметром *rs:ParameterLanguage*интерпретируется независимо от браузера. Например, если на сервере отчетов установлены региональные параметры «Немецкий», но пользователь обращается к отчету по URL-адресу из браузера, в котором установлены региональные параметры «Английский (США)», то значения параметров, передаваемые на сервер отчетов, будут обрабатываться неправильно.  
  
 Рассмотрим следующий URL-адрес отчета:  
  
```  
https://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 В этом случае сервер, на котором установлен региональный стандарт «de-de», создает URL-адрес посредством подписки по электронной почте или через гиперссылку. Гиперссылка показывает, что для отчета необходимо передать параметр даты начала (4 октября 2008 г.) и дату окончания (11 октября 2008 г.) в соответствии с немецкими стандартами даты и времени. Однако пользователь, выполняющий доступ по URL-адресу из браузера, где установлен стандарт «en-us», принудительно вызывает на сервере интерпретацию значений в соответствии со стандартами даты и времени, принятыми в США, в результате чего получаются значения 10 апреля 2008 г. и 10 ноября 2008 г. Чтобы решить эту проблему, можно использовать параметр *rs:ParameterLanguage* , переопределяющий язык браузера для интерпретации параметров:  
  
```  
https://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 Дополнительно к значениям **true** и **false** для параметра доступа по URL-адресу *rc:Parameters*теперь можно передавать значение **Collapsed**. Если в URL-адресе используется значение *rc:Parameters*=**Collapsed** , область параметров в средстве просмотра HTML-страниц сворачивается, но пользователь может ее включить. Значение **false** полностью удаляет область параметров с панели инструментов средства просмотра HTML-страниц и делает ее недоступной для пользователя.  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
