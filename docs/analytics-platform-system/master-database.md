---
title: "База данных master (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c71617c0-6689-4f52-81c6-58f4cf7c7377
caps.latest.revision: "8"
ms.workload: not set
ms.openlocfilehash: 1fde1a329703ed833a9fdeb6686b1a63c04aea79
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="master-database"></a>База данных master
База данных master SQL Server PDW сохраняет сведения об имени входа уровня устройства и каталоге базы данных. Это основной базы данных SQL Server, расположенный на узел элемента управления. Таким образом он предоставляет аналогичные функциональные возможности в SQL Server PDW как обеспечивает master для SQL Server.  
  
Дополнительные сведения о системных баз данных см. в разделе [системных баз данных](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Следующий список описывает операции, которые невозможно выполнить в базе данных master SQL Server PDW.  
  
Вы *нельзя:*  
  
-   Выполните разностной резервной копии базы данных master.  
  
-   Создайте пользовательские объекты в базе данных master.  
  
-   Изменение параметров сортировки базы данных master.  
  
-   Изменение владельца базы данных master.  
  
-   Удалите или переименуйте master.  
  
-   Изменение разрешений для образца.  
  
-   Выполнение **: параметр DBCC**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Задача|Description|  
|--------|---------------|  
|Создание полной резервной копии базы данных master.|Пример<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Дополнительные сведения см. в разделе [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Восстановление базы данных master|Чтобы восстановить базу данных master, используйте [восстановление базы данных Master](restore-the-master-database.md) в программе Configuration Manager.|  
|Просмотр сведений о каталоге базы данных.|`SELECT * FROM master.sys.databases;`|  
|Просмотр сведений имя входа и разрешения во всей системе.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
