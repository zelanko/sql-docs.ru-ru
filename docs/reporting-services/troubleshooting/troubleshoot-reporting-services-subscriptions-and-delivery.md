---
title: "Устранение неполадок с подписками и доставкой служб Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 05/31/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: troubleshooting
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1775f7-9919-48ca-8bd7-cc16df274e2c
caps.latest.revision: "16"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9ebea5b20a98810b9a680f476bfa0bd94ffbf7e7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="troubleshoot-reporting-services-subscriptions-and-delivery"></a>Устранение неполадок, связанных с подписками и доставкой служб Reporting Services
  
    
В этой статье приведены инструкции по устранению неполадок, которые могут возникать при работе с подписками на отчеты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] , расписаниями и доставкой.  
## <a name="log-information"></a>Сведения о журнале
 
На странице "Подписка" в [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] указано состояние подписки, однако при наличии проблем с подпиской подробные сведения см. в журналах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . 
![ssrs_tutorial_datadriven_subscription_status_ReportManager](../../reporting-services/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.png)

**Журналы трассировки.** Журналы трассировки — это текстовые файлы, записываемые в папку: `\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`

Ниже представлен пример записи журнала.

```
   subscription WindowsService_10   4c7c    05/24/2016-01:05:06  e ERROR     Failure writing file \\ServerName\SalesReports\so71949.xls : Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareProvider+NetworkErrorException: An impersonation error occurred using the security context of the current user. ---> System.ArgumentException: Value does not fall within the expected range.  05/24/2016
```
Дополнительные сведения о журналах трассировки [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] см. в разделе: 
+ [Журнал трассировки сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)
+ [Файлы журнала служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)

**Представления журнала выполнения:**

Журналы выполнения являются представлениями в базе данных ReportServer SQL. Дополнительные сведения о [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] см. в разделе [Представления ExecutionLog и ExecutionLog3 служб Reporting Services](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

----------
## <a name="unable-to-send-reports-using-e-mail-with-windows-server-2003-and-pop3"></a>Не удается отправить отчеты по электронной почте в системе Windows Server 2003 по протоколу POP3  
Если приложение электронной почты использует протокол POP3 в системе Microsoft Windows Server 2003, отправка отчетов через локальный POP3-сервер может оказаться невозможной. Если на сервере отчетов настроена отправка электронной почты с помощью локального сервера POP3 и создана подписка, отправляющая отчет, то может возвращаться следующее сообщение об ошибке:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Failure sending mail: <error message>`  
  
здесь \<сообщение_об_ошибке> заменяется дополнительными сведениями об ошибке, возвращенными объектами данных совместной работы (CDO).  
  
### <a name="to-resolve-this-problem"></a>Чтобы разрешить эту проблему:  
* Установите значение элемента `SendUsing` в файле **RSReportServer.config** равным 1.  
* Очистите значение свойства `SMTPServer` , чтобы оно стало пустым. Кроме того, задайте значение свойства `SMTPServerPickupDirectory` .   
  
Дополнительные сведения об использовании локальной службы SMTP для доставки отчетов по электронной почте см. в документации по настройке сервера отчетов для работы с электронной почтой.  
  
## <a name="failure-sending-mail-the-server-rejected-the-sender-address-the-server-response-was-454-573-client-does-not-have-permission-to-submit-mail-to-this-server"></a>Сбой при отправке электронной почты: сервер отклонил адрес отправителя. Получен ответ сервера: 454 5.7.3. У клиента отсутствует разрешение на отправку почты на данный сервер.  
Эта ошибка возникает, когда настройки политики безопасности на SMTP-сервере позволяют передавать почту для последующей доставки только пользователям, прошедшим проверку. Если SMTP-сервер не принимает сообщений электронной почты от анонимных пользователей, обратитесь к системному администратору для получения разрешения на использование сервера.  
> Эта ошибка также возникает, если в качестве SMTPServer задан сервер Exchange. Для отправки почты с помощью сервера Exchange необходимо указать имя шлюза SMTP, настроенного для сервера Exchange. Соответствующие данные можно получить у администратора сервера Exchange.  
  
## <a name="subscriptions-are-not-processing"></a>Подписки не обрабатываются  
Обработка подписок может завершаться неуспешно в следующих случаях:   
* Расписание запуска отчета устарело. Возможно, расписание для подписок, запускающих обновление моментального снимка отчета, устарело.  
  
* Сервер отчетов, агент SQL или серверное приложение электронной почты не запущены.  
* Невозможно доставить отчет (например, слишком большой размер отчета). Чтобы определить, действительно ли отправка невозможна из-за слишком большого размера отчета, сохраните отчет в файле и затем отправьте его по электронной почте. Выберите тот же формат представления, который был указан в подписке. Если будет получена ошибка доставки, используйте вместо модуля доставки по электронной почте сервера отчетов модуль доставки в общую папку.  
* Компьютер, используемый для доставки в общую папку, выключен, либо общая папка доступна только для чтения.  
* Модуль доставки, заданный в подписке, удален или отключен.  
* Значения учетных данных изменены с хранимых на интегрированные или запрашиваемые.  
* Имя аргумента или тип данных в определении отчета были изменены, а отчет опубликован повторно. Если подписка содержит параметр, который стал недопустимым, то она становится неактивной.  
  
Дополнительные сведения см. в вики-статье TechNet [Устранение неполадок и ошибок служб Reporting Services](http://social.technet.microsoft.com/wiki/contents/articles/1633.ssrs-troubleshoot-issues-and-errors-with-reporting-services.aspx).  
  
  
    
  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]

