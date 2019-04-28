---
title: Восстановление базы данных master - Analytics Platform System | Документация Майкрософт
description: Восстановление базы данных master в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678432"
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Восстановление базы данных master в Analytics Platform System
**Восстановление базы данных Master** страница SQL Server PDW Configuration Manager позволяет восстановить базу данных master из резервной копии.  
  
## <a name="before-you-begin"></a>Перед началом  
  
> [!IMPORTANT]  
> Чтобы выполнить восстановление, SQL Server PDW необходимо удалить текущей базе данных master, которая содержит сведения о безопасности пользователя и каталоге базы данных. Мы рекомендуем, создания резервной копии текущей базы данных master, прежде чем выполнять восстановление.  
  
## <a name="to-restore-the-master-database"></a>Восстановление базы данных master  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager щелкните **восстановление базы данных Master**.  
  
3.  Выберите главный резервную копию для восстановления.  
  
4.  Нажмите кнопку **Применить**.  
  
5.  Чтобы выполнить восстановление, SQL Server PDW завершать работу всех служб на устройство и отключите всех пользователей. После завершения восстановления, SQL Server PDW будет перезапустить службы устройство.  
  
![Восстановление PDW устройств DWConfig устройство базы данных master](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
