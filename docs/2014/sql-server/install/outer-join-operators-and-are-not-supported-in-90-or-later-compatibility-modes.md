---
title: Операторы внешнего соединения *= и =* не поддерживаются в режиме совместимости 90 и более поздних версий | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47a58b60ecd303b893e001663134d9b510bbabfa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194860"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Операторы внешнего соединения *= и =* не поддерживаются в режиме совместимости 90 или выше.
  Советник по переходу обнаружил использование операторов внешнего соединения * = и =\*. Эти операторы не поддерживаются в режиме совместимости 90 и выше. При обновлении пользовательские базы данных сохраняют свой режим совместимости. Инструкции, использующие эти операторы, завершатся ошибкой.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед изменением уровня совместимости базы данных 90 или более поздней версии, измените инструкции, использующие операторы внешнего соединения * = и =\* использовать эквивалентные ключевые слова OUTER JOIN. В следующем примере показан запрос, использующий оператор `*=`, и эквивалентный ему запрос, использующий ключевые слова `LEFT OUTER JOIN`.  
  
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
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
