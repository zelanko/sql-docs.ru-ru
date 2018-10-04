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
manager: craigg
ms.openlocfilehash: c4f13a77a9f03aa76fccc41a1fa19878dd935db0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636812"
---
# <a name="recordset-related-error-information"></a>Сведения о связанных с наборами записей ошибках
Во время пакетной обработки, **состояние** свойство **записей** объект предоставляет сведения об отдельных записей в **записей**. До выполнения пакетного обновления, **состояние** свойство **записей** отражает сведения о записях, которые нужно добавить, изменен или удален. После **UpdateBatch** был вызван, **состояние** свойство указывающее на успешное или неуспешное выполнение операции. При переходе от записи к записи **записей**, значение **состояние** изменения свойств для описания состояния текущей записи.
