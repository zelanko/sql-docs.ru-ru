---
title: "Сведения об ошибке, относящееся к набору записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da70765b3dd273cb5671e539cb856334529db4e0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-related-error-information"></a>Сведения об ошибке, относящееся к набору записей
Во время пакетной обработки **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. Прежде чем пакетного обновления выполняется **состояние** свойство **набора записей** отражает сведения о записях, которые нужно добавить, изменить или удалить. После **UpdateBatch** был вызван, **состояние** свойство указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
