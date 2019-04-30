---
title: Запуск и остановка службы сервера отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4bd22faaa9d0f3b6ce213c37e20615492b1e95d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190814"
---
# <a name="start-and-stop-the-report-server-service"></a>Запуск и остановка службы сервера отчетов
  Сервер отчетов реализован в виде службы Windows, которая включает веб-службу сервера отчетов, диспетчер отчетов и приложение фоновой обработки. Чтобы использовать какие-либо функции сервера отчетов, эта служба должна работать. Остановка службы приводит к прекращению всех операций сервера отчетов.  
  
 Пока служба остановлена, запросы для запланированных отчетов и обработки подписок, которые были бы удовлетворены, если бы служба работала, добавляются в очередь. Это связано с тем, что задания, выполняемые агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , создают события. Если требуется предотвратить создание незавершенных операций во время простоя службы, рассмотрите возможность остановить работу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Чтобы запустить или остановить службу сервера отчетов, можно применить ряд средств, включая программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и оснастку «Службы», существующую в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Чтобы выполнить какие-либо другие операции, кроме запуска и остановки службы, например для смены учетной записи службы, необходимо пользоваться программой настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Использование для смены учетной записи службы других средств может привести к неработоспособности установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
