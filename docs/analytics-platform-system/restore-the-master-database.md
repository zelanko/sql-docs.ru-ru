---
title: Восстановление базы данных master — система аналитики (ТД) | Документация Майкрософт
description: Восстановите базу данных master в системе аналитики платформы (ТД).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 624e1199fb953945ae6476a1f935dded48508bab
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176136"
---
# <a name="restore-the-master-database-in-analytics-platform-system-aps"></a>Восстановление базы данных master в системе аналитики (ТД)
**Главная страница восстановления** SQL Server PDW Configuration Manager позволяет восстановить базу данных master из резервной копии.  
  
## <a name="before-you-begin"></a>Перед началом  
  
> [!IMPORTANT]  
> Чтобы выполнить восстановление, SQL Server PDW необходимо удалить текущую базу данных master, содержащую сведения о безопасности пользователя и каталог базы данных. Перед выполнением восстановления рекомендуется создать резервную копию текущей базы данных master.  
  
## <a name="to-restore-the-master-database"></a>Восстановление базы данных master  
  
1.  Запустите Configuration Manager. Дополнительные сведения см. [в статье Запуск платформы &#40;&#41;Configuration Manager Analytics](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager щелкните Restore Master ( **восстановить образец**).  
  
3.  Выберите базу данных master для восстановления.  
  
4.  Нажмите кнопку **Применить**.  
  
5.  Чтобы выполнить восстановление, SQL Server PDW завершит работу всех служб устройств и отключит всех пользователей. После завершения восстановления SQL Server PDW перезапустит службы устройств.  
  
![Мастер восстановления DWConfig устройства PDW](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
