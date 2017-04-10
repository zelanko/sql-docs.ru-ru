---
title: "Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)
  Данные, собранные управляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], хранятся в хранилище данных управления для программы (UMDW), имя файла UMDW — sysutility_mdw.  
  
 Можно задать сроком хранения данных в UMDW. Дополнительные сведения см. в разделе [Администрирование программ (служебная программа SQL Server)](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md).  
  
 Перечисленные далее параметры конфигурации не могут быть изменены в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Имя UMDW: Sysutility_mdw.  
  
-   Частота передачи набора элементов сбора: каждые 15 минут.  
  
 Каталог UMDW можно настроить: \<системный диск>:\Program Files\Microsoft SQL Server\MSSQL10_50.\<имя_UCP>\MSSQL\Data\\, где \<системный диск> — это чаще всего диск C:\. Файл журнала, Sysutility_mdw_\<GUID>_LOG, находится в том же каталоге.  
  
> [!NOTE]  
>  Расположение файла UMDW (sysutility_mdw) можно изменить путем отсоединения и присоединения или с помощью инструкции ALTER DATABASE. Рекомендуется использовать инструкцию ALTER DATABASE. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  