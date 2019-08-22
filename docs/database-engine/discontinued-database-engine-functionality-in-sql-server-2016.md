---
title: Неподдерживаемые функции ядра СУБД в SQL Server 2016 | Документы Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 99a7b94a45b1baf0ffbf1a491a0387ef11108ebd
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69494085"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2016"></a>Нерекомендуемые функции ядра СУБД в SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны функции компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , которые больше не доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql15includessssql15-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
- [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] — это 64-разрядное приложение. 32-разрядная установка больше не поддерживается, хотя некоторые элементы работают как 32-разрядные.  
  
- Уровень совместимости 90 не поддерживается. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

- Подсистема ActiveX не поддерживается. Используйте вместо нее командную строку или скрипты PowerShell.

- Параметры запуска **-h** и **-g**. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/database-engine-service-startup-options?view=sql-server-2014).
  
## <a name="previous-versions"></a>Предыдущие версии  
  
- [Неподдерживаемые функции ядра СУБД в SQL Server 2014](https://docs.microsoft.com/sql/database-engine/discontinued-database-engine-functionality-in-sql-server-2016?view=sql-server-2014)

## <a name="see-also"></a>См. также:  
 [Нерекомендуемые функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Устаревшие функции репликации в SQL Server](../relational-databases/replication/deprecated-features-in-sql-server-replication.md)  
  
 
