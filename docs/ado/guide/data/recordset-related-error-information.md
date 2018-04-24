---
title: Сведения об ошибке, относящееся к набору записей | Документы Microsoft
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
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9a4f68dfffa07f79bdd53e380b68f55d3a01dfe
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="recordset-related-error-information"></a>Сведения об ошибке, относящееся к набору записей
Во время пакетной обработки **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. Прежде чем пакетного обновления выполняется **состояние** свойство **набора записей** отражает сведения о записях, которые нужно добавить, изменить или удалить. После **UpdateBatch** был вызван, **состояние** свойство указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
