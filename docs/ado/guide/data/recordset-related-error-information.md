---
description: Сведения о связанных с наборами записей ошибках
title: Сведения об ошибке, связанные с набором записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 454c62b969ee69e6186792ce77873c8c8fbb5704
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979815"
---
# <a name="recordset-related-error-information"></a>Сведения о связанных с наборами записей ошибках
Во время пакетной обработки свойство **Status** объекта **Recordset** предоставляет сведения об отдельных записях в **наборе**записей. Перед обновлением пакетного обновления свойство **Status** **набора записей** отражает сведения о добавляемых, изменяемых и удаленных записях. После вызова **UpdateBatch** свойство **Status** указывает на успешное или неуспешное выполнение операции. При переходе от записи к записи в **наборе записей**значение свойства **Status** изменяется, чтобы описать состояние текущей записи.
