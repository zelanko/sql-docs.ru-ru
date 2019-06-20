---
title: Указание ключевого слова WITH при использовании табличных подсказок в режиме совместимости 90 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff2fee26c6f71cc398f8dbacf91f3ad8dbdb3358
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092163"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>Указание ключевого слова WITH при использовании табличных подсказок в режиме совместимости 90
  С некоторыми исключениями в предложении FROM запроса поддерживаются табличные указания только с ключевым словом WITH. Дополнительные сведения см. в разделах «FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])» и «Табличные указания [!INCLUDE[tsql](../../includes/tsql-md.md)]» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Запросы, содержащие табличные указания в предложении FROM, необходимо изменить, включив перед табличными указаниями ключевое слово WITH.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
