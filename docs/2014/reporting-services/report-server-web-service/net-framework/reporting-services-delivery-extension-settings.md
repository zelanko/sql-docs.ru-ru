---
title: Параметры модуля доставки служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
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
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 0bd8ee198a2627d9caaba340c4357bb0de0f30aa
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014805"
---
# <a name="reporting-services-delivery-extension-settings"></a>Параметры модулей доставки служб Reporting Services
  В [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включены модуль доставки по электронной почте и модуль доставки в общую папку. Доставка по электронной почте позволяет переслать отчет отдельным пользователям или группам по электронной почте. Доставка в общую папку позволяет автоматически отправлять подготовленные отчеты в сетевую папку. Любой из поддерживаемых модулей доставки можно использовать со стандартными подписками или с управляемыми данными подписок. Настройки доставки, характерные для типа модуля доставки, передаются при каждом вызове методов <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> и <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Для получения списка настроек доставки программным образом можно использовать метод <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Настройки модуля доставки учитывают регистр.  
  
## <a name="e-mail-delivery-settings"></a>Настройки доставки электронной почты  
 В следующей таблице перечисляются настройки доставки для подписок, использующих электронную почту сервера отчетов.  
  
|Параметр|Значение|  
|-------------|-----------|  
|**Кому**|Адрес электронной почты, отображаемый в строке `To` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Обязательный.|  
|**Копия**|Адрес электронной почты, отображаемый в строке `Cc` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Необязательный.|  
|**Скрытая копия**|Адрес электронной почты, отображаемый в строке `Bcc` в сообщении электронной почты. Несколько адресов разделяются точками с запятой. Необязательный.|  
|**ReplyTo**|Адрес электронной почты, отображаемый в заголовке `Reply-To` сообщения электронной почты. Значение должно быть одиночным адресом электронной почты. Необязательный.|  
|`IncludeReport`|Значение, показывающее, необходимо ли включать отчет в доставку по электронной почте. Значение `true` указывает, что отчет доставляется в тексте сообщения электронной почты.|  
|**RenderFormat**|Имя модуля подготовки отчетов, используемого для создания подготовленного отчета. Имя должно соответствовать одному из видимых модулей подготовки отчетов, установленных на сервере отчетов. Данное значение необходимо, если для параметра `IncludeReport` установлено значение `true`.|  
|**Приоритет**|Приоритет отправки сообщения электронной почты. Допустимые значения: `LOW`, `NORMAL` и `HIGH`. Значение по умолчанию — `NORMAL`.|  
|**Тема**|Текст в строке темы сообщения электронной почты.|  
|**Комментарий**|Текст, включенный в тело сообщения электронной почты.|  
|**IncludeLink**|Значение, показывающее, необходимо ли включать ссылку на отчет в текст сообщения.|  
  
## <a name="file-share-delivery-settings"></a>Параметры доставки в общую папку  
 В следующей папке перечисляются параметры доставки в общую папку для подписок.  
  
|Параметр|Значение|  
|-------------|-----------|  
|**FILENAME**|Имя файла, сохраняемого на диск.|  
|**FILEEXTN**|Указывает, стоит ли включать расширение файла в отчет, готовый для просмотра. Имеет значение `true` или `false`.|  
|**PATH**|Путь папки или путь общей папки в формате UNC, в которую будет сохранен отчет.|  
|**RENDER_FORMAT**|Формат отчета, сохраняемого на диск.|  
|**USERNAME**|Имя пользователя, необходимое для доступа к сетевому ресурсу или диску.|  
|**PASSWORD**|Пароль, необходимый для доступа к сетевому ресурсу или диску.|  
|**WRITEMODE**|Режим записи, используемый при доступе к диску. Допустимые значения: `None`, `Overwrite` и `AutoIncrement`.|  
  
## <a name="see-also"></a>См. также  
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
