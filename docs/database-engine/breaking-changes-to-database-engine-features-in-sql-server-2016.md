---
title: Критические изменения в функциях ядра СУБД в SQL Server 2016 | Документы Майкрософт
ms.custom: ''
ms.date: 11/27/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3074eb04df91d5284d5943b09a9c7c59bd9ef6f2
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983155"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Критические изменения в функциях ядра СУБД в SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны критические изменения в компоненте [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] и предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы.  
  
##  <a name="SQL15"></a> Критические изменения в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   Столбец *sample_ms* таблицы `sys.dm_io_virtual_file_stats` был расширен с типа данных **int** до **bigint**.  
  
-   Столбец *TimeStamp* таблицы `sys.fn_virtualfilestats` был расширен с типа данных **int** до **bigint**.  

-   При уровне совместимости базы данных 130 неявные преобразования типов данных из **datetime** в **datetime2** демонстрируют повышенную точность благодаря учету долей миллисекунд. В результате преобразования дают иные значения. Всегда используйте явное приведение к типу данных datetime2, когда имеется сценарий смешанного сравнения типов данных datetime и datetime2. Дополнительные сведения см. в этой [статье службы поддержки Майкрософт](https://support.microsoft.com/help/4010261).

-   При уровне совместимости базы данных 130 операции, которые выполняют неявные преобразования между определенными числовыми типами и типами данных даты и времени, демонстрируют повышенную точность и могут привести к иным преобразованным значениям. Это включает использование функций, которые требуют вычислений, таких как, например, `DATEDIFF` и `ROUND`. Дополнительные сведения см. в этой [статье службы поддержки Майкрософт](https://support.microsoft.com/help/4010261).

## <a name="previous-versions"></a> Предыдущие версии  

Сведения о критических изменениях в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и в некоторых более ранних версиях см. в статье [Критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014).

#### <a name="archived-documentation-for-very-old-versions-of-sql-server"></a>Архивная документация по очень старым версиям SQL Server

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Неподдерживаемые функции ядра СУБД в SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Обратная совместимость компонента ядра СУБД SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Улучшения SQL Server 2016 или SQL Server 2017 в Windows для обработки некоторых типов данных и нестандартных операций](https://support.microsoft.com/help/4010261)   
