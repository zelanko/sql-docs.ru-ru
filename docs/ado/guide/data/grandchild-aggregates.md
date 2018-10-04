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
manager: craigg
ms.openlocfilehash: f1bff3c8a155e1e9378acbb659f00817f478382e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602383"
---
# <a name="grandchild-aggregates"></a>Статистические выражения внучатых элементов
Глава столбец, созданный в предложении команды фигуры может предоставляться *Глава псевдоним* (обычно с ключевым словом AS). Можно указать любой столбец в любой главе форму **записей** с полным именем, которое идентифицирует дочерний элемент, которая содержит столбец. Например если родительского главе, chap1, содержит дочерние Глава, chap2, имеющей столбец amount, amt, то полное имя будет chap1.chap2.amt. Полное имя затем может использоваться в качестве аргумента одному из агрегатные функции (SUM, AVG, MAX, MIN, COUNT, STDEV или любой).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
