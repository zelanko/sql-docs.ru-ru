---
title: Восстановление базы данных master - система платформы аналитики | Документы Microsoft
description: Восстановите базу данных master в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Восстановите базу данных master в система платформы аналитики
**Восстановление базы данных Master** страница SQL Server PDW Configuration Manager позволяет восстановить базу данных master из резервной копии.  
  
## <a name="before-you-begin"></a>Перед началом  
  
> [!IMPORTANT]  
> Для выполнения восстановления, SQL Server PDW необходимо удалить текущий основной базы данных, содержащей сведения о безопасности пользователя, а также каталог базы данных. Рекомендуется выровнять перед восстановлением резервной копии текущей базы данных master.  
  
## <a name="to-restore-the-master-database"></a>Восстановление базы данных master  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустите диспетчер конфигурации &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager щелкните **восстановление базы данных Master**.  
  
3.  Выберите главный резервную копию для восстановления.  
  
4.  Нажмите кнопку **Применить**.  
  
5.  Для выполнения восстановления, SQL Server PDW завершить работу всех служб на устройство и отключите всех пользователей. После завершения восстановления SQL Server PDW перезагрузится служб устройства.  
  
![Master, восстановить PDW устройств DWConfig](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
