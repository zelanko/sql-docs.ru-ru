---
title: Выполнение действий после установки | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: distributed-replay
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 12bdc7fbea96f7af42f7b2a1f175e58fc03c0b6c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="complete-the-post-installation-steps"></a>Выполнение действий после установки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После установки компонента распределенного воспроизведения следует изменить учетные записи служб клиента и контроллера распределенного воспроизведения.  
  
### <a name="to-complete-the-post-installation-steps"></a>Выполнение действий после установки  
  
1.  **Создание правил брандмауэра**: На компьютерах контроллера и клиента в брандмауэре необходимо разрешить входящий трафик для соответствующей службы. Укажите правила брандмауэра для исполняемых файлов службы, расположенных в установочных папках.  
  
    1.  Для службы контроллера создайте правило для файла **DReplayController.exe**, расположенного в папке установки. Например, следующая команда включает это правило, где `%InstallPath%` — папка установки службы:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Для службы клиента на каждом клиентском компьютере создайте правило для файла **DReplayClient.exe**, расположенного в папке установки. Например, следующая команда включает это правило, где `%InstallPath%` — папка установки службы:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Предоставьте каждому клиенту разрешения на целевом сервере**. После завершения установки службы клиента на клиентских компьютерах следует вручную добавить учетные записи службы клиента в роль sysadmin на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Для установки компонентов распределенного воспроизведения необходимо обладать разрешениями администратора. Только имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разрешениями sysadmin может добавлять учетные записи службы клиента в роль sysadmin тестового сервера. Дополнительные сведения о вопросах безопасности распределенного воспроизведения см. в разделе [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  
