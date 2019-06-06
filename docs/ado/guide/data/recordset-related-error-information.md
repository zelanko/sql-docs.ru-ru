---
title: Сведения об ошибках, относящихся к набору записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ef5f6cc4a262cecc81a8dd72f2d3e3f6a7e2fded
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700421"
---
# <a name="recordset-related-error-information"></a>Сведения о связанных с наборами записей ошибках
Во время пакетной обработки, **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. До выполнения пакетного обновления, **состояние** свойство **записей** отражает сведения о записях, которые нужно добавить, изменен или удален. После **UpdateBatch** был вызван, **состояние** свойство указывающее на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
