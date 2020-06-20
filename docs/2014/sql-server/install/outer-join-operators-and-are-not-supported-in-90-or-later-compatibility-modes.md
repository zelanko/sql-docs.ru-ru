---
title: Операторы внешнего объединения *= и =* не поддерживаются в режимах совместимости 90 и более поздних версий | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 357c729e6d53cc17f2e4c169dd66613b6cfd2f5d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065261"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Операторы внешнего соединения \*= и =\* не поддерживаются в режиме совместимости 90 и выше
  Советник по переходу обнаружил использование операторов внешнего объединения \* = и = \* . Эти операторы не поддерживаются в режиме совместимости 90 и выше. При обновлении пользовательские базы данных сохраняют свой режим совместимости. Инструкции, использующие эти операторы, завершатся ошибкой.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Прежде чем изменить режим совместимости базы данных на 90 или более поздней версии, измените инструкции, использующие операторы внешнего объединения \* = и =, \* для использования эквивалентных ключевых слов внешнего объединения. В следующем примере показан запрос, использующий оператор `\*=`, и эквивалентный ему запрос, использующий ключевые слова `LEFT OUTER JOIN`.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Дополнительные сведения о внешних соединениях см. в разделе «Использование внешних соединений» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
