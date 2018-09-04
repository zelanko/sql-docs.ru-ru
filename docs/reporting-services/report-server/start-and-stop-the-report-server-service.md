---
title: Запуск и остановка службы сервера отчетов | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: df012a7c922a6b329eef6b7c47547fef19faae64
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43270189"
---
# <a name="start-and-stop-the-report-server-service"></a>Запуск и остановка службы сервера отчетов
  Сервер отчетов реализован в виде службы Windows, которая включает веб-службу сервера отчетов, диспетчер отчетов и приложение фоновой обработки. Чтобы использовать какие-либо функции сервера отчетов, эта служба должна работать. Остановка службы приводит к прекращению всех операций сервера отчетов.  
  
 Пока служба остановлена, запросы для запланированных отчетов и обработки подписок, которые были бы удовлетворены, если бы служба работала, добавляются в очередь. Это связано с тем, что задания, выполняемые агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , создают события. Если требуется предотвратить создание незавершенных операций во время простоя службы, рассмотрите возможность остановить работу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Чтобы запустить или остановить службу сервера отчетов, можно применить ряд средств, включая программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и оснастку «Службы», существующую в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Чтобы выполнить какие-либо другие операции, кроме запуска и остановки службы, например для смены учетной записи службы, необходимо пользоваться программой настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Использование для смены учетной записи службы других средств может привести к неработоспособности установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
 Эту службу нельзя приостанавливать и возобновлять, и параметров запуска она не имеет. Хотя явные зависимости отсутствуют, для поддержки подписок и проводимых по расписанию операций с отчетами на сервере отчетов должен работать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a>Запуск или остановка службы с помощью программы настройки служб Reporting Services  
  
1.  Запустите программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к серверу отчетов.  
  
2.  На странице состояния сервера отчетов нажмите **Остановить** или **Запустить**.  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a>Запуск или остановка службы с помощью оснастки «Службы» в разделе «Администрирование»  
  
-   В окне "Администрирование" откройте оснастку "Службы", щелкните правой кнопкой мыши элемент **Службы SQL Server Reporting Services (MSSQLSERVER)** и выберите команду **Стоп** или **Перезапустить**.  
  
 Если используется несколько экземпляров параллельно или сервер отчетов работает в качестве именованного экземпляра, убедитесь в том, что имя экземпляра в круглых скобках соответствует экземпляру сервера отчетов, который планируется остановить или перезапустить.  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a>Запуск или остановка службы с помощью диспетчера конфигурации SQL Server  
  
1.  Запуск диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Выберите "Службы SQL Server", щелкните правой кнопкой мыши элемент **SQL Server Reporting Services**и выберите команду **Стоп** или **Перезапустить**.  
  
## <a name="see-also"></a>См. также:  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Запуск, остановка или приостановка службы агента SQL Server](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
