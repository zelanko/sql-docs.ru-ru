---
title: Сведения об ошибке, относящееся к набору записей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dab1996d2915757ba6e7834b5e41bd6eade41c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-related-error-information"></a>Сведения об ошибке, относящееся к набору записей
Во время пакетной обработки **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. Прежде чем пакетного обновления выполняется **состояние** свойство **набора записей** отражает сведения о записях, которые нужно добавить, изменить или удалить. После **UpdateBatch** был вызван, **состояние** свойство указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
