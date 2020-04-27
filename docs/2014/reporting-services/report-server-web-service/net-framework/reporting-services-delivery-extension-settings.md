---
title: Параметры модуля доставки служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d356bc1cb981479de8a4b1baa3bdaaf45b6145ca
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63260751"
---
# <a name="reporting-services-delivery-extension-settings"></a>Параметры модулей доставки служб Reporting Services
  В [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включены модуль доставки по электронной почте и модуль доставки в общую папку. Доставка по электронной почте позволяет переслать отчет отдельным пользователям или группам по электронной почте. Доставка в общую папку позволяет автоматически отправлять подготовленные отчеты в сетевую папку. Любой из поддерживаемых модулей доставки можно использовать со стандартными подписками или с управляемыми данными подписок. Настройки доставки, характерные для типа модуля доставки, передаются при каждом вызове методов <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> и <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Для получения списка настроек доставки программным образом можно использовать метод <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Настройки модуля доставки учитывают регистр.  
  
## <a name="e-mail-delivery-settings"></a>Настройки доставки электронной почты  
 В следующей таблице перечисляются настройки доставки для подписок, использующих электронную почту сервера отчетов.  
  
|Параметр|Применение|  
|-------------|-----------|  
|**Кому**|Адрес электронной почты, отображаемый в строке `To` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Обязательный элемент.|  
|**КОМУ**|Адрес электронной почты, отображаемый в строке `Cc` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Необязательный параметр.|  
|**Скрытая копия**|Адрес электронной почты, отображаемый в строке `Bcc` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Необязательный параметр.|  
|**ReplyTo**|Адрес электронной почты, отображаемый в заголовке `Reply-To` сообщения электронной почты. Значение должно быть одиночным адресом электронной почты. Необязательный параметр.|  
|`IncludeReport`|Значение, показывающее, необходимо ли включать отчет в доставку по электронной почте. Значение `true` указывает, что отчет доставляется в тексте сообщения электронной почты.|  
|**RenderFormat**|Имя модуля подготовки отчетов, используемого для создания подготовленного отчета. Имя должно соответствовать одному из видимых модулей подготовки отчетов, установленных на сервере отчетов. Данное значение необходимо, если для параметра `IncludeReport` установлено значение `true`.|  
|**Priority**|Приоритет отправки сообщения электронной почты. Допустимые значения: `LOW`, `NORMAL` и `HIGH`. Значение по умолчанию — `NORMAL`.|  
|**Тема**|Текст в строке темы сообщения электронной почты.|  
|**Комментарий**|Текст, включенный в тело сообщения электронной почты.|  
|**IncludeLink**|Значение, показывающее, необходимо ли включать ссылку на отчет в текст сообщения.|  
  
## <a name="file-share-delivery-settings"></a>Параметры доставки в общую папку  
 В следующей папке перечисляются параметры доставки в общую папку для подписок.  
  
|Параметр|Применение|  
|-------------|-----------|  
|**ФАЙЛОВ**|Имя файла, сохраняемого на диск.|  
|**FILEEXTN**|Указывает, стоит ли включать расширение файла в отчет, готовый для просмотра. Имеет значение `true` или `false`.|  
|**ПУТЬ**|Путь папки или путь общей папки в формате UNC, в которую будет сохранен отчет.|  
|**RENDER_FORMAT**|Формат отчета, сохраняемого на диск.|  
|**ИМЕН**|Имя пользователя, необходимое для доступа к сетевому ресурсу или диску.|  
|**ПАРОЛЬ**|Пароль, необходимый для доступа к сетевому ресурсу или диску.|  
|**WRITEMODE**|Режим записи, используемый при доступе к диску. Допустимые значения: `None`, `Overwrite` и `AutoIncrement`.|  
  
## <a name="see-also"></a>См. также  
 [Технический справочник &#40;SSRS&#41;](../../technical-reference-ssrs.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
