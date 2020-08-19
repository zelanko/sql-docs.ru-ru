---
description: Сведения о связанных с наборами записей ошибках
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7806d446c200f4d90ec458ceea268435ad9994e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452956"
---
# <a name="recordset-related-error-information"></a>Сведения о связанных с наборами записей ошибках
Во время пакетной обработки свойство **Status** объекта **Recordset** предоставляет сведения об отдельных записях в **наборе**записей. Перед обновлением пакетного обновления свойство **Status** **набора записей** отражает сведения о добавляемых, изменяемых и удаленных записях. После вызова **UpdateBatch** свойство **Status** указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи в **наборе записей**значение свойства **Status** изменяется, чтобы описать состояние текущей записи.
