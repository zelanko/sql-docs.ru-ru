---
title: Восстановление базы данных Master (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7870021a-0d89-422e-b8ea-1cc95b45c139
caps.latest.revision: 11
ms.openlocfilehash: 0f1acb692198873897d5dc26e2074beab4517e44
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="restore-the-master-database"></a>Восстановление базы данных Master
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
  
![DWConfig Appliance PDW Restore master](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
