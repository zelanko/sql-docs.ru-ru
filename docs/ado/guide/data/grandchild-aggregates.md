---
title: Агрегаты внучатый | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925231"
---
# <a name="grandchild-aggregates"></a>Статистические выражения внучатых элементов
Столбцу раздела, созданному в предложении команды Shape, может быть присвоено *имя-псевдоним главы* (обычно с ключевым словом AS). Можно определить любой столбец в любой главе **набора записей** в форме с полным именем, определяющим дочерний элемент, содержащий столбец. Например, если родительская глава, Chap1, содержит дочернюю главу Chap2, имеющую столбец Amount, то полное имя будет Chap1. Chap2. AMT. Полное имя может использоваться в качестве аргумента для одной из агрегатных функций (SUM, AVG, MAX, MIN, COUNT, STDEV или ANY).  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
