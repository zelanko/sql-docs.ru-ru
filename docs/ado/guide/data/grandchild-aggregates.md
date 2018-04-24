---
title: Статистические выражения по внукам | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 589bece101c52a38d11f10a5d5f8f162aa3af8ad
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="grandchild-aggregates"></a>Статистические выражения по внукам
Столбец в предложении фигуру, команда может присваиваться *главе псевдоним* (обычно с ключевым словом AS). Можно указать любой столбец в любой главе форму **записей** с полным именем, которое идентифицирует дочерний элемент, содержащую столбец. Например если родительский главе, chap1, содержит главе дочерних, chap2, имеет столбец amount amt, то полное имя будет chap1.chap2.amt. Полное имя затем может использоваться как аргумент для какого-либо агрегатные функции (SUM, AVG, MAX, MIN, COUNT, STDEV или все).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
