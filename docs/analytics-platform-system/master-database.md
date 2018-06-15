---
title: База данных master - Parallel Data Warehouse | Документы Microsoft
description: Дополнительные сведения о базе данных master в Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bf07b9c27e08a49cb0866b177a0ec37fed4528a0
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538544"
---
# <a name="master-database---parallel-data-warehouse"></a>База данных master - Parallel Data Warehouse
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
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Описание|  
|--------|---------------|  
|Создание полной резервной копии базы данных master.|Пример<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Дополнительные сведения см. в разделе [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Восстановление базы данных master|Чтобы восстановить базу данных master, используйте [восстановление базы данных Master](restore-the-master-database.md) в программе Configuration Manager.|  
|Просмотр сведений о каталоге базы данных.|`SELECT * FROM master.sys.databases;`|  
|Просмотр сведений имя входа и разрешения во всей системе.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
