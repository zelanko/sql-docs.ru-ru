---
title: Клиентские протоколы — свойства TCP/IP (вкладка "Протокол") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: configuration-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6a3228a1815675fe413fd244ac222234397cc3ae
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="client-protocols---tcp-ip-properties-protocol-tab"></a>Клиентские протоколы — свойства TCP/IP (вкладка "Протокол")
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** в диалоговом окне **Свойства TCP/IP** , чтобы просмотреть или задать указанные ниже параметры. Чтобы подключиться к другому порту, введите номер порта в поле **Порт по умолчанию** . Дополнительные сведения о строках подключения см. в разделе [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Параметры  
 **Порт по умолчанию**  
 Указывает порт, который сетевая библиотека TCP/IP использует для попытки подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение порта по умолчанию равно 1433.  
  
 При подключении к экземпляру по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]клиент использует это значение. Если экземпляр по умолчанию был настроен для прослушивания другого порта, измените это значение на соответствующий номер порта.  
  
 При подключении к именованному экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]клиент будет пытаться получить номер порта от службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенной на компьютере сервера. Если служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущена, номер порта должен предоставляться через этот параметр или как часть строки соединения.  
  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Keep Alive**  
 Этот параметр (в миллисекундах) управляет частотой попыток протокола TCP проверить работоспособность неактивного соединения путем отправки пакета **KEEPALIVE** . Значение по умолчанию — 30 000 миллисекунд.  
  
 **Интервал проверки активности**  
 Этот параметр (в миллисекундах) определяет интервал, разделяющий повторные передачи пакета **KEEPALIVE** , пока не происходит получение ответа. Значение по умолчанию — 1 000 миллисекунд.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Создание псевдонима (вкладка "Псевдоним")](../../tools/configuration-manager/new-alias-alias-tab.md)   
 [Свойства &#60;Псевдоним&#62; (вкладка "Псевдоним")](../../tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
