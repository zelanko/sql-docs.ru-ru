---
title: Восстановление базы данных master
description: Восстановите базу данных master в системе аналитики платформы (ТД).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6d122881f5283da86f66494ee2f049756d151551
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400456"
---
# <a name="restore-the-master-database-in-analytics-platform-system-aps"></a>Восстановление базы данных master в системе аналитики (ТД)
**Главная страница восстановления** SQL Server PDW Configuration Manager позволяет восстановить базу данных master из резервной копии.  
  
## <a name="before-you-begin"></a>Перед началом  
  
> [!IMPORTANT]  
> Чтобы выполнить восстановление, SQL Server PDW необходимо удалить текущую базу данных master, содержащую сведения о безопасности пользователя и каталог базы данных. Перед выполнением восстановления рекомендуется создать резервную копию текущей базы данных master.  
  
## <a name="to-restore-the-master-database"></a>Восстановление базы данных master  
  
1.  Запустите Configuration Manager. Дополнительные сведения см. [в статье запуск Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager щелкните **RESTORE MASTER (восстановить образец**).  
  
3.  Выберите базу данных master для восстановления.  
  
4.  Нажмите кнопку **Применить**.  
  
5.  Чтобы выполнить восстановление, SQL Server PDW завершит работу всех служб устройств и отключит всех пользователей. После завершения восстановления SQL Server PDW перезапустит службы устройств.  
  
![Восстановление базы данных master PDW устройств DWConfig](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
