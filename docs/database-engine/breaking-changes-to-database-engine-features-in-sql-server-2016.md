---
title: Критические изменения в функциях ядра СУБД в SQL Server 2016 | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: 144
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2b43a8008fcfddc43cad78b049483b6ff3b1fb75
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40406800"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Критические изменения в функциях ядра СУБД в SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этой статье описаны критические изменения в компоненте [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] и предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы.  
  
##  <a name="SQL15"></a> Критические изменения в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   Столбец sample_ms column of sys.dm_io_virtual_file_stats был расширен с типа данных **int** до **bigint** .  
  
-   Столбец TimeStamp в sys.fn_virtualfilestats был расширен с типа данных **int** до **bigint** .  

-   Для использования хэш-алгоритмов MD2, MD4, MD5, SHA или SHA1 (не рекомендуется) необходимо задать уровень совместимости базы данных ниже 130.  

-   При уровне совместимости базы данных 130 неявные преобразования типов данных из **datetime** в **datetime2** демонстрируют повышенную точность благодаря учету долей миллисекунд. В результате преобразования дают иные значения. Всегда используйте явное приведение к типу данных datetime2, когда имеется сценарий смешанного сравнения типов данных datetime и datetime2. Дополнительные сведения см. в [этой статье](http://support.microsoft.com/help/4010261) на сайте службы поддержки Майкрософт.
  
## <a name="previous-versions"></a>Предыдущие версии  
  
-   [Критические изменения в функциях ядра СУБД в SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md))  
  
-   [Критические изменения в функциях ядра СУБД в SQL Server 2012](breaking-changes-to-database-engine-features-in-sql-server-2016.md))  
  
-   [Критические изменения в функциях ядра СУБД в SQL Server 2008](breaking-changes-to-database-engine-features-in-sql-server-2016.md))  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Неподдерживаемые функции ядра СУБД в SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Обратная совместимость компонента ядра СУБД SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Улучшения SQL Server 2016 или SQL Server 2017 в Windows для обработки некоторых типов данных и нестандартных операций](http://support.microsoft.com/help/4010261)
  
  
