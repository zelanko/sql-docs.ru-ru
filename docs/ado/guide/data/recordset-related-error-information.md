---
title: Сведения об ошибке, связанные с набором записей | Документация Майкрософт
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
ms.openlocfilehash: d3f8e8d9802b5d0c73af73aff20d929c188b9292
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924376"
---
# <a name="recordset-related-error-information"></a>Сведения о связанных с наборами записей ошибках
Во время пакетной обработки свойство **Status** объекта **Recordset** предоставляет сведения об отдельных записях в **наборе**записей. Перед обновлением пакетного обновления свойство **Status** **набора записей** отражает сведения о добавляемых, изменяемых и удаленных записях. После вызова **UpdateBatch** свойство **Status** указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи в **наборе записей**значение свойства **Status** изменяется, чтобы описать состояние текущей записи.
