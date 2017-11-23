---
title: "Число записей | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11c30fb4abfeab58b1a6ea650bc41ce1f72524e0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="record-count"></a>Число записей
Поле заголовка дескриптора SQL_DESC_COUNT — это от единицы индекс наибольший номер записи, которая содержит данные. Это поле не является количеством всех столбцов или параметров, связанных. При выделении дескриптор SQL_DESC_COUNT начальное значение — 0.  
  
 Драйвер принимает любое действие для выделения и обслуживания в хранилище, он требуется для хранения информации дескриптора. Приложение явно не указать размер дескриптора не выделяют новых записей. Если приложение предоставляет сведения для записи дескриптор, номер которого выше, чем значение SQL_DESC_COUNT, драйвер автоматически увеличивается SQL_DESC_COUNT. Если приложение отменяет привязку записи дескриптора наибольший номер, драйвер автоматически уменьшается SQL_DESC_COUNT содержать количество наибольший оставшиеся присоединенной записи.
