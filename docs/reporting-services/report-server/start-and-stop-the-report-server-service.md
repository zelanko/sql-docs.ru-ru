---
title: Запуск и остановка службы сервера отчетов | Документы Майкрософт
ms.date: 05/21/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6463dc7e4b17992138a61e6a37277149fccfda68
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66270203"
---
# <a name="start-and-stop-the-report-server-service"></a>Запуск и остановка службы сервера отчетов

  Сервер отчетов реализован в виде службы Windows, которая включает в себя веб-службу сервера отчетов, веб-портал и приложение фоновой обработки. Чтобы использовать какие-либо функции сервера отчетов, эта служба должна работать. Остановка службы приводит к прекращению всех операций сервера отчетов.  
  
 Пока служба остановлена, запросы для запланированных отчетов и обработки подписок, которые были бы удовлетворены, если бы служба работала, добавляются в очередь. Это связано с тем, что задания, выполняемые агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , создают события. Если требуется предотвратить создание незавершенных операций во время простоя службы, рассмотрите возможность остановить работу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Чтобы запустить или остановить службу сервера отчетов, можно применить ряд средств, включая программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и оснастку «Службы», существующую в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 Чтобы выполнить какие-либо другие операции, кроме запуска и остановки службы, например для смены учетной записи службы, необходимо пользоваться программой настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Использование для смены учетной записи службы других средств может привести к неработоспособности установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
 Эту службу нельзя приостанавливать и возобновлять, и она не имеет параметров запуска. Хотя явные зависимости отсутствуют, для поддержки подписок и проводимых по расписанию операций с отчетами на сервере отчетов должен работать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="use-the-reporting-services-configuration-tool"></a>Использование программы настройки служб Reporting Services  
  
1. Запустите программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к серверу отчетов.  
  
2. На странице состояния сервера отчетов нажмите **Остановить** или **Запустить**.  
  
## <a name="use-administrative-tools"></a>Использование средств администрирования  

- В окне "Администрирование" откройте оснастку "Службы", щелкните правой кнопкой мыши элемент **Службы SQL Server Reporting Services (MSSQLSERVER)** и выберите **Остановить** или **Перезапустить**.  
  
- Если используется несколько экземпляров параллельно или сервер отчетов работает в качестве именованного экземпляра, убедитесь в том, что имя экземпляра в круглых скобках соответствует экземпляру сервера отчетов, который планируется остановить или перезапустить.  
  
## <a name="see-also"></a>См. также раздел  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Запуск, остановка или приостановка службы агента SQL Server](https://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  