---
description: Статистические выражения внучатых элементов
title: Агрегаты внучатый | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: rothja
ms.author: jroth
ms.openlocfilehash: 02d481e55fa8fc41e022d41b88c9dcd6c4777dfe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980715"
---
# <a name="grandchild-aggregates"></a>Статистические выражения внучатых элементов
Столбцу раздела, созданному в предложении команды Shape, может быть присвоено *имя-псевдоним главы* (обычно с ключевым словом AS). Можно определить любой столбец в любой главе **набора записей** в форме с полным именем, определяющим дочерний элемент, содержащий столбец. Например, если родительская глава, Chap1, содержит дочернюю главу Chap2, имеющую столбец Amount, то полное имя будет Chap1. Chap2. AMT. Полное имя может использоваться в качестве аргумента для одной из агрегатных функций (SUM, AVG, MAX, MIN, COUNT, STDEV или ANY).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](./data-shaping-example.md)