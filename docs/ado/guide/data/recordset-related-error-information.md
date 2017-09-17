---
title: "Сведения об ошибке, относящееся к набору записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279fcc0564f433234cbac730465e2af06a7eb5e7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-related-error-information"></a>Сведения об ошибке, относящееся к набору записей
Во время пакетной обработки **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. Прежде чем пакетного обновления выполняется **состояние** свойство **набора записей** отражает сведения о записях, которые нужно добавить, изменить или удалить. После **UpdateBatch** был вызван, **состояние** свойство указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
