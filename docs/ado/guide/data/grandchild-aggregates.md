---
title: Статистические выражения внучатых элементов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac0b06479b3ad4feedaa63bdac227d028b7a9e09
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925231"
---
# <a name="grandchild-aggregates"></a>Статистические выражения внучатых элементов
Глава столбец, созданный в предложении команды фигуры может предоставляться *Глава псевдоним* (обычно с ключевым словом AS). Можно указать любой столбец в любой главе форму **записей** с полным именем, которое идентифицирует дочерний элемент, которая содержит столбец. Например если родительского главе, chap1, содержит дочерние Глава, chap2, имеющей столбец amount, amt, то полное имя будет chap1.chap2.amt. Полное имя затем может использоваться в качестве аргумента одному из агрегатные функции (SUM, AVG, MAX, MIN, COUNT, STDEV или любой).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
