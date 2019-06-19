---
title: Операторы внешнего соединения *= и =* не поддерживаются в режиме совместимости 90 и выше | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 62a6f9e016abf24f28660b04e7a6242fdd6606ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093688"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Операторы внешнего соединения \*= и =\* не поддерживаются в режиме совместимости 90 и выше
  Помощник по обновлению обнаружил использование операторов внешнего соединения \*= и =\*. Эти операторы не поддерживаются в режиме совместимости 90 и выше. При обновлении пользовательские базы данных сохраняют свой режим совместимости. Инструкции, использующие эти операторы, завершатся ошибкой.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед изменением режима совместимости базы данных 90 или более поздней версии, измените инструкции, использующие операторы внешнего соединения \*= и =\* использовать эквивалентные ключевые слова OUTER JOIN. В следующем примере показан запрос, использующий оператор `\*=`, и эквивалентный ему запрос, использующий ключевые слова `LEFT OUTER JOIN`.  
  
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
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
