---
title: Сведения об ошибке, относящееся к набору записей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
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
ms.openlocfilehash: 55f64646050eba8c76432c68c39b36b0daa9f4be
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272353"
---
# <a name="recordset-related-error-information"></a>Сведения об ошибке, относящееся к набору записей
Во время пакетной обработки **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. Прежде чем пакетного обновления выполняется **состояние** свойство **набора записей** отражает сведения о записях, которые нужно добавить, изменить или удалить. После **UpdateBatch** был вызван, **состояние** свойство указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
