---
title: Клиентские протоколы — свойства TCP и IP (вкладка «Протокол») | Документация Майкрософт
description: Узнайте, как указать параметры TCP/IP в Microsoft SQL Server Configuration Manager, например параметр проверки активности и номер порта по умолчанию.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 32e1546af52fb411564c2b6d1635971b9f73fc60
ms.sourcegitcommit: c8e45e0fdab8ea2ae1c7e709346354576b18ca1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716681"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>Клиентские протоколы — свойства TCP/IP (вкладка "Протокол")
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** в диалоговом окне **Свойства TCP/IP**, чтобы просмотреть или задать указанные ниже параметры. Чтобы подключиться к другому порту, введите номер порта в поле **Порт по умолчанию** . Дополнительные сведения о строках подключения см. в разделе [Создание допустимой строки подключения с использованием протокола TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Варианты  
 **Порт по умолчанию**  
 Указывает порт, который сетевая библиотека TCP/IP использует для попытки подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение порта по умолчанию равно 1433.  
  
 При подключении к экземпляру по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]клиент использует это значение. Если экземпляр по умолчанию был настроен для прослушивания другого порта, измените это значение на соответствующий номер порта.  
  
 При подключении к именованному экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]клиент будет пытаться получить номер порта от службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенной на компьютере сервера. Если служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запущена, номер порта должен предоставляться через этот параметр или как часть строки соединения.  
  
 **Enabled**  
 Возможные значения: **Да** и **нет**.  
  
 **Keep Alive**  
 Этот параметр (в миллисекундах) управляет частотой попыток протокола TCP проверить работоспособность неактивного соединения путем отправки пакета **KEEPALIVE** . Значение по умолчанию — 30 000 миллисекунд.  
  
 **Интервал проверки активности**  
 Этот параметр (в миллисекундах) определяет интервал, разделяющий повторные передачи пакета **KEEPALIVE** , пока не происходит получение ответа. Значение по умолчанию — 1 000 миллисекунд.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Новый псевдоним &#40;вкладка Псевдоним&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [Свойства &#60;Псевдоним&#62; (вкладка "Псевдоним")](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
