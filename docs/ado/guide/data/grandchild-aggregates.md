---
title: "Статистические выражения по внукам | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8889be6c78765d7eadf211016de92d041c9419f3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="grandchild-aggregates"></a>Статистические выражения по внукам
Столбец в предложении фигуру, команда может присваиваться *главе псевдоним* (обычно с ключевым словом AS). Можно указать любой столбец в любой главе форму **записей** с полным именем, которое идентифицирует дочерний элемент, содержащую столбец. Например если родительский главе, chap1, содержит главе дочерних, chap2, имеет столбец amount amt, то полное имя будет chap1.chap2.amt. Полное имя затем может использоваться как аргумент для какого-либо агрегатные функции (SUM, AVG, MAX, MIN, COUNT, STDEV или все).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
