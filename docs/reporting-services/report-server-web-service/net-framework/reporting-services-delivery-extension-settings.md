---
title: "Настройки модуля доставки служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
caps.latest.revision: 36
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 668c3d31af5f287d7d254c2dc666e20a5f6328fa
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-delivery-extension-settings"></a>Параметры модулей доставки служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]включает модуль доставки по электронной почте и модуль доставки общую папку. Доставка по электронной почте позволяет переслать отчет отдельным пользователям или группам по электронной почте. Доставка в общую папку позволяет автоматически отправлять подготовленные отчеты в сетевую папку. Любой из поддерживаемых модулей доставки можно использовать со стандартными подписками или с управляемыми данными подписок. Настройки доставки, характерные для типа модуля доставки, передаются при каждом вызове методов <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> и <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Для получения списка настроек доставки программным образом можно использовать метод <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Настройки модуля доставки учитывают регистр.  
  
## <a name="e-mail-delivery-settings"></a>Настройки доставки электронной почты  
 В следующей таблице перечисляются настройки доставки для подписок, использующих электронную почту сервера отчетов.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**КОМУ**|Адрес электронной почты, который отображается на **для** строки сообщения электронной почты. Несколько адресов разделяются точками с запятой. Обязательный.|  
|**КОПИЯ**|Адрес электронной почты, который отображается на **Cc** строки сообщения электронной почты. Несколько адресов разделяются точками с запятой. Необязательно.|  
|**СКРЫТАЯ КОПИЯ**|Адрес электронной почты, который отображается на **СК** строки сообщения электронной почты. Несколько адресов разделяются точками с запятой. Необязательно.|  
|**ReplyTo**|Адрес электронной почты, который отображается в **ответить** заголовка сообщения электронной почты. Значение должно быть одиночным адресом электронной почты. Необязательно.|  
|**IncludeReport**|Значение, показывающее, необходимо ли включать отчет в доставку по электронной почте. Значение **true** указывает, что отчет доставляется в тексте сообщения электронной почты.|  
|**RenderFormat**|Имя модуля подготовки отчетов, используемого для создания подготовленного отчета. Имя должно соответствовать одному из видимых модулей подготовки отчетов, установленных на сервере отчетов. Это значение является обязательным, если **IncludeReport** параметру было присвоено значение **true**.|  
|**Приоритет**|Приоритет отправки сообщения электронной почты. Допустимые значения: **LOW**, **ОБЫЧНЫЙ**, и **высокой**. Значение по умолчанию — **ОБЫЧНЫЙ**.|  
|**Тема**|Текст в строке темы сообщения электронной почты.|  
|**Комментарий**|Текст, включенный в тело сообщения электронной почты.|  
|**IncludeLink**|Значение, показывающее, необходимо ли включать ссылку на отчет в текст сообщения.|  
  
## <a name="file-share-delivery-settings"></a>Параметры доставки в общую папку  
 В следующей папке перечисляются параметры доставки в общую папку для подписок.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**ИМЯ ФАЙЛА**|Имя файла, сохраняемого на диск.|  
|**FILEEXTN**|Указывает, стоит ли включать расширение файла в отчет, готовый для просмотра. Имеет значение **true** или **false**.|  
|**ПУТЬ**|Путь папки или путь общей папки в формате UNC, в которую будет сохранен отчет.|  
|**RENDER_FORMAT**|Формат отчета, сохраняемого на диск.|  
|**ИМЯ ПОЛЬЗОВАТЕЛЯ**|Имя пользователя, необходимое для доступа к сетевому ресурсу или диску.|  
|**ПАРОЛЬ**|Пароль, необходимый для доступа к сетевому ресурсу или диску.|  
|**ПАРАМЕТР**|Режим записи, используемый при доступе к диску. Допустимые значения: **нет**, **перезаписи**, и **AutoIncrement**.|  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
