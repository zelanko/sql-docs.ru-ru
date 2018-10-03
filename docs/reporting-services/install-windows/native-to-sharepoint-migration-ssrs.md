---
title: Миграция из собственного режима в режим интеграции с SharePoint (SSRS) | Документы Майкрософт
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7adb637db4c3b9bcf7350589ac1ff352e8ec9cd2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701482"
---
# <a name="native-to-sharepoint-migration-ssrs"></a>Миграция из собственного режима в режим интеграции с SharePoint (SSRS)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Выполнить обновление или преобразование из одного режима сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в другой невозможно. Например, невозможно обновить или преобразовать сервер отчетов в собственном режиме в сервер, работающий в режиме интеграции с SharePoint. Невозможно копировать базы данных сервера отчетов между режимами, потому что они используют различные схемы баз данных. Можно перенести содержимое с одного сервера отчетов на другой. Используемые средства зависят от режима сервера отчетов, настроенного для исходных и целевых серверов.  
  
##  <a name="bkmk_native_to_sharepoint"></a> Средство миграции служб Reporting Services  
 Средство поддерживает перенос содержимого из развертывания в собственном режиме в развертывание в режиме интеграции с SharePoint. Эта программа не поддерживает перенос из режима интеграции с SharePoint в режим SharePoint или из режима интеграции с SharePoint в собственный режим.  
  
 См. дополнительные сведения о [средстве миграции служб Reporting Services](http://www.microsoft.com/download/details.aspx?id=29560) (http://www.microsoft.com/download/details.aspx?id=29560).  
  
## <a name="use-script-to-migrate-content"></a>Использование скрипта для переноса содержимого  
 Если средство миграции не удовлетворяет требованиям, можно вручную перенести данные сервера отчетов. Ниже приводится сводка шагов, которые необходимо выполнить для переноса элементов отчета из одного развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в другое. Метод поддерживает собственный режим работы и режим интеграции с SharePoint в качестве исходного и конечного сервера.  
  
1.  Создание резервных копий и восстановление ключей шифрования. Это ключ, который используется для шифрования данных. Ключ шифрования также используется для шифрования паролей, например паролей, сохраненных для соединения с источниками данных. Но перенести пароли невозможно, поэтому в целевой среде их нужно ввести снова.  
  
2.  **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .** Запишите скрипт Visual Basic, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Используйте служебную программу **RS.exe** для запуска скрипта. Программа RS.exe устанавливается вместе c [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    -   [Sample Reporting Services rs.exe Script to Copy Content between Report Servers](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). Разделы содержат описание того, как использовать образец скрипта, который можно загрузить на сайте CodePlex.  
  
    -   Пример rss-скрипта на сайте CodePlex см. здесь: [Скрипт программы RS.exe служб Reporting Services, который переносит содержимое с одного сервера отчетов на другой](http://azuresql.codeplex.com/releases/view/115207)  
  
    -   [Сценарии и PowerShell со службами Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md)  
  
 В следующей таблице перечислены объекты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые можно перенести с помощью скриптов.  
  
|Объект|Можно вносить в скрипт|Комментарии|  
|------------|---------------------|--------------|  
|Отчеты|Да|После миграции потребуется повторно ввести пароли для источников данных.|  
|Источники данных|Да|После миграции восстановите ссылки отчетов на источники данных.|  
|Модели|Да||  
|Наборы данных|Да||  
|Элементы отчетов||После миграции проверьте или обновите путь к элементам отчета.|  
|Расписания|Да|См. метод ListSchedules в разделе [Subscription and Delivery Methods](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md).|  
|Подписки|Да|См. метод List Subscriptions [Subscription and Delivery Methods](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md) и метод <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A> .|  
|Моментальные снимки|||

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
