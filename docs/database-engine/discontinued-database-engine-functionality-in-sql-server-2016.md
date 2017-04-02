---
title: "Нерекомендуемые функции ядра СУБД в SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VIA, протокол"
  - "неподдерживаемые возможности [SQL Server]"
  - "Служба SQL Mail"
  - "неподдерживаемая функциональность [SQL Server]"
  - "RESTORE WITH DBO_ONLY"
  - "BACKUP WITH PASSWORD"
  - "пользовательские экземпляры включены"
  - "BACKUP WITH MEDIAPASSWORD"
  - "AWE"
  - "SQL-DMO"
  - "*= и =*"
  - "Уровни совместимости 80"
  - "COMPUTE BY"
  - "истечение срока ожидания пользовательского экземпляра"
  - "sp_dropalias"
  - "COMPUTE"
  - "WITH APPEND"
  - "sys.database_principal_aliases"
  - "sp_dboption"
  - "DATABASEPROPERTY"
  - "Подсказка FASTFIRSTROW"
  - "SET DISABLE_DEF_CNST_CHK"
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
caps.latest.revision: 100
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 100
---
# Нерекомендуемые функции ядра СУБД в SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны функции компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , которые больше не доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql15tokensssql15mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] — это 64-разрядное приложение. 32-разрядная установка больше не поддерживается, хотя некоторые элементы работают как 32-разрядные.  
  
-   Уровень совместимости 90 не поддерживается. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md).  

-   Подсистема ActiveX не поддерживается. Используйте вместо нее командную строку или скрипты PowerShell.
  
## <a name="previous-versions"></a>Предыдущие версии  
  
-   [Неподдерживаемые функции ядра СУБД в SQL Server 2014](https://msdn.microsoft.com/library/ms144262\(v=sql.120\))  
  
-   [Неподдерживаемые функции ядра СУБД в SQL Server 2012](https://msdn.microsoft.com/library/ms144262\(v=sql.110\))  
  
-   [Неподдерживаемые функции ядра СУБД в SQL Server 2008](https://msdn.microsoft.com/library/ms144262\(v=sql.100\))  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Устаревшие функции репликации в SQL Server](../relational-databases/replication/deprecated-features-in-sql-server-replication.md)  
  
 