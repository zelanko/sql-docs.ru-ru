---
title: "Выполнение действий после установки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 375f63cb25259ca3bfcc966d6b41809ad1fa992b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="complete-the-post-installation-steps"></a>Выполнение действий после установки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]После установки компонентов распределенного воспроизведения следует изменить учетные записи служб клиента и контроллера распределенного воспроизведения.  
  
### <a name="to-complete-the-post-installation-steps"></a>Выполнение действий после установки  
  
1.  **Создание правил брандмауэра**: На компьютерах контроллера и клиента в брандмауэре необходимо разрешить входящий трафик для соответствующей службы. Укажите правила брандмауэра для исполняемых файлов службы, расположенных в установочных папках.  
  
    1.  Для службы контроллера создайте правило для файла **DReplayController.exe**, расположенного в папке установки. Например, следующая команда включает это правило, где `%InstallPath%` — папка установки службы:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Для службы клиента на каждом клиентском компьютере создайте правило для файла **DReplayClient.exe**, расположенного в папке установки. Например, следующая команда включает это правило, где `%InstallPath%` — папка установки службы:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Предоставьте каждому клиенту разрешения на целевом сервере**. После завершения установки службы клиента на клиентских компьютерах следует вручную добавить учетные записи службы клиента в роль sysadmin на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Для установки компонентов распределенного воспроизведения необходимо обладать разрешениями администратора. Только имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разрешениями sysadmin может добавлять учетные записи службы клиента в роль sysadmin тестового сервера. Дополнительные сведения о вопросах безопасности распределенного воспроизведения см. в разделе [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  
