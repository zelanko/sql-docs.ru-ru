---
title: Миграция из собственного режима в режим интеграции с SharePoint (SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adf6b91b1c83f490ffe6c85fecd374fca7c1a085
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253181"
---
# <a name="native-to-sharepoint-migration-ssrs"></a>Миграция из собственного режима в режим интеграции с SharePoint (SSRS)
  Выполнить обновление или преобразование из одного режима сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в другой невозможно. Например, невозможно обновить или преобразовать сервер отчетов в собственном режиме в сервер, работающий в режиме интеграции с SharePoint. Невозможно копировать базы данных сервера отчетов между режимами, потому что они используют различные схемы баз данных. Можно перенести содержимое с одного сервера отчетов на другой. Используемые средства зависят от режима сервера отчетов, настроенного для исходных и целевых серверов.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint  
  
##  <a name="bkmk_native_to_sharepoint"></a> Средство миграции служб Reporting Services  
 Средство поддерживает перенос содержимого из развертывания в собственном режиме в развертывание в режиме интеграции с SharePoint. Эта программа не поддерживает перенос из режима интеграции с SharePoint в режим SharePoint или из режима интеграции с SharePoint в собственный режим.  
  
 См. дополнительные сведения о [средстве миграции служб Reporting Services](https://www.microsoft.com/download/details.aspx?id=29560) (https://www.microsoft.com/download/details.aspx?id=29560).  
  
## <a name="use-script-to-migrate-content"></a>Использование скрипта для переноса содержимого  
 Если средство миграции не удовлетворяет требованиям, можно вручную перенести данные сервера отчетов. Ниже приводится сводка шагов, которые необходимо выполнить для переноса элементов отчета из одного развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в другое. Метод поддерживает собственный режим работы и режим интеграции с SharePoint в качестве исходного и конечного сервера.  
  
1.  Создание резервных копий и восстановление ключей шифрования. Это ключ, который используется для шифрования данных. Ключ шифрования также используется для шифрования паролей, например паролей, сохраненных для соединения с источниками данных. Но перенести пароли невозможно, поэтому в целевой среде их нужно ввести снова.  
  
2.  **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .** Запишите скрипт Visual Basic, который вызывает методы SOAP веб-службы сервера отчетов, чтобы копировать данные между базами данных. Используйте служебную программу **RS.exe** для запуска скрипта. Программа RS.exe устанавливается вместе c [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    -   [Пример Reporting Services сценария RS. exe для переноса содержимого между серверами отчетов](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). Разделы содержат описание того, как использовать образец скрипта, который можно загрузить на сайте CodePlex.  
  
    -   Пример rss-скрипта на сайте CodePlex см. здесь: [Скрипт программы RS.exe служб Reporting Services, который переносит содержимое с одного сервера отчетов на другой](https://azuresql.codeplex.com/releases/view/115207)  
  
    -   [Работа с отчетами и PowerShell в Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md)  
  
 В следующей таблице перечислены объекты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые можно перенести с помощью скриптов.  
  
|Объект|Можно вносить в скрипт|Комментарии|  
|------------|---------------------|--------------|  
|Отчеты|Да|После миграции потребуется повторно ввести пароли для источников данных.|  
|Источники данных|Да|После миграции восстановите ссылки отчетов на источники данных.|  
|Модели|Да||  
|Наборы данных|Да||  
|Элементы отчетов||После миграции проверьте или обновите путь к элементам отчета.|  
|Расписания|Да|См. метод ListSchedules в разделе [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md).|  
|Подписки|да|См. метод List Subscriptions [Subscription, методы доставки](../report-server-web-service/methods/subscription-and-delivery-methods.md) и метод ChangeSubscriptionOwner.<xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>|  
|Моментальные снимки|||  
||||  
  
