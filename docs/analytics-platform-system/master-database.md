---
title: База данных master
description: Дополнительные сведения о базе данных master см. в статье Параллельное хранилище данных.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: cafef8a5b702b6df4475d34e9395bb12bc9461fb
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400978"
---
# <a name="master-database---parallel-data-warehouse"></a>База данных master — Параллельное хранилище данных
База данных SQL Server PDW Master хранит сведения для входа на уровне устройства и каталог базы данных. Это база данных SQL Server master, которая находится на узле управления. Таким образом, он предоставляет аналогичные функции для SQL Server PDW, как главный предоставляет SQL Server.  
  
Дополнительные сведения о системных базах данных см. в разделе [системные базы данных](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
В следующем списке описываются операции, которые нельзя выполнить в базе данных master SQL Server PDW.  
  
Вы *не можете:*  
  
-   Выполните разностное резервное копирование главной реплики.  
  
-   Создание объектов User в Master.  
  
-   Измените параметры сортировки для Master.  
  
-   Изменение владельца главного.  
  
-   Удаление или переименование главного сервера.  
  
-   Измените разрешения на Master.  
  
-   Выполните **инструкцию DBCC SHRINKLOG**.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Описание|  
|--------|---------------|  
|Создайте полную резервную копию главной реплики.|Пример:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Дополнительные сведения см. в разделе [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Восстановление базы данных master|Чтобы восстановить базу данных master, воспользуйтесь страницей [Восстановление базы данных master](restore-the-master-database.md) в средстве Configuration Manager.|  
|Просмотр сведений о каталоге базы данных.|`SELECT * FROM master.sys.databases;`|  
|Просмотр имени входа и сведений о разрешениях на уровне системы.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
