---
title: "Критические изменения в функциях ядра СУБД в SQL Server 2016 | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/15/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: 144
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f45be24e7164076948dbfa28702311dd9641eae7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Критические изменения в функциях ядра СУБД в SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этой статье описаны критические изменения в компоненте [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] и предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы.  
  
##  <a name="SQL15"></a> Критические изменения в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   Столбец sample_ms column of sys.dm_io_virtual_file_stats был расширен с типа данных **int** до **bigint** .  
  
-   Столбец TimeStamp в sys.fn_virtualfilestats был расширен с типа данных **int** до **bigint** .  

-   Для использования хэш-алгоритмов MD2, MD4, MD5, SHA или SHA1 (не рекомендуется) необходимо задать уровень совместимости базы данных ниже 130.  

-   При уровне совместимости базы данных 130 неявные преобразования типов данных из **datetime** в **datetime2** демонстрируют повышенную точность благодаря учету долей миллисекунд. В результате преобразования дают иные значения. Всегда используйте явное приведение к типу данных datetime2, когда имеется сценарий смешанного сравнения типов данных datetime и datetime2.

  
## <a name="previous-versions"></a>Предыдущие версии  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Неподдерживаемые функции ядра СУБД в SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Обратная совместимость компонента ядра СУБД SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

