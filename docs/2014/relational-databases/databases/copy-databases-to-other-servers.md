---
title: Копирование баз данных на другие серверы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb10b485f7cf0a4517cbe3967d28d704d0abe6fc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195374"
---
# <a name="copy-databases-to-other-servers"></a>Копирование баз данных на другие серверы
  В некоторых случаях можно скопировать базу данных с одного компьютера на другой и использовать ее для тестирования, проверки согласованности данных, разработки ПО, выполнения отчетов, создания зеркальной базы данных или предоставления доступа к базе данных сотрудникам удаленного филиала.  
  
 Скопировать базу данных можно одним из следующих способов.  
  
-   Использование мастера копирования баз данных  
  
     Мастер копирования баз данных можно использовать для копирования или перемещения баз данных между серверами, а также для обновления базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до более новой версии. Дополнительные сведения см. в статье [Use the Copy Database Wizard](use-the-copy-database-wizard.md).  
  
-   Восстановление базы данных из резервной копии  
  
     Чтобы копировать целую базу данных, можно использовать инструкции BACKUP и RESTORE языка [!INCLUDE[tsql](../../includes/tsql-md.md)] . Выбор методики восстановления базы данных из полной резервной копии для копирования базы данных с одного компьютера на другой может быть мотивирован разными причинами. Сведения о копировании базы данных путем восстановления из резервной копии см. в статье [Копирование баз данных путем создания и восстановления резервных копий](copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Чтобы настроить зеркальную базу данных для зеркального отображения базы данных, необходимо восстановить базу данных на зеркальном сервере с помощью инструкции RESTORE DATABASE *<имя_базы_данных>* WITH NORECOVERY. Дополнительные сведения см. в разделе [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Использование мастера создания скриптов для публикации баз данных  
  
     Мастер создания скриптов позволяет передать базу данных с локального компьютера на веб-поставщик услуг размещения. Дополнительные сведения см. в статье [Мастер формирования и публикации скриптов](../scripting/generate-and-publish-scripts-wizard.md).  
  
  
