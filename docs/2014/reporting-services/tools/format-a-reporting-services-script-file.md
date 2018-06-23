---
title: Форматирование файла скрипта служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: fd49c4cb6e16c9bbda6dc970e3bb5b0ceb2ef52d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102588"
---
# <a name="format-a-reporting-services-script-file"></a>Форматирование файла скрипта служб Reporting Services
  Скрипт служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это файл кода [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET, написанный для прокси-сервера, построенного на основе языка описания веб-служб (язык WSDL), определяющего API-интерфейс протокола простого доступа к объектам служб Reporting Services (SOAP). Файл скрипта хранится как текстовый файл Юникод или UTF-8 с расширением RSS.  
  
 Файл скрипта действует как модуль языка [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Он может содержать пользовательские процедуры и переменные уровня модуля. Для успешного выполнения файла скрипта он должен содержать главную процедуру. Главная процедура — это первая процедура, к которой идет обращение при запуске файла скрипта. В ней можно создавать операции веб-службы и запускать определяемые пользователем подпроцедуры. Следующий фрагмент кода создает главную процедуру:  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 Среда скриптов автоматически соединяется с сервером отчетов, создает класс-посредник и формирует ссылку на переменную (*rs*) для объекта записи-посредника веб-службы. Отдельные создаваемые инструкции должны ссылаться только на переменную уровня модуля *rs* , для выполнения любых операций веб-службы, доступных в библиотеке веб-службы. Следующий код на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] вызывает метод <xref:ReportService2010.ReportingService2010.ListChildren%2A> веб-службы из файла скрипта:  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  Учетные данные пользователей находятся под управлением среды скриптов и передаются через аргументы командной строки с помощью программы RS.exe. Хотя проверку подлинности веб-службы можно задать с помощью переменной *rs* , рекомендуется использовать среду скриптов. Внутри самого файла скрипта выполнять проверку подлинности веб-службы не требуется. Дополнительные сведения о проверке подлинности среду скриптов см. в разделе [программы RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md).  
  
 Пространства имен не объявляются в файлах скриптов. Среда скриптов предоставляет доступ к нескольким полезным пространствам имен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] : **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**и **System.IO**.  
  
 Образцы скриптов см. на странице [Образцы продуктов служб SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также  
 [Веб-служба сервера отчетов](../report-server-web-service/report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../technical-reference-ssrs.md)   
 [Служебная программа RS.exe (SSRS)](rs-exe-utility-ssrs.md)  
  
  