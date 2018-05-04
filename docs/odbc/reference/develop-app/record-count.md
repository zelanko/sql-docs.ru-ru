---
title: Число записей | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca1ed60d44b1c8133c51e78a769ca6d92d9bb6b0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="record-count"></a>Число записей
Поле заголовка дескриптора SQL_DESC_COUNT — это от единицы индекс наибольший номер записи, которая содержит данные. Это поле не является количеством всех столбцов или параметров, связанных. При выделении дескриптор SQL_DESC_COUNT начальное значение — 0.  
  
 Драйвер принимает любое действие для выделения и обслуживания в хранилище, он требуется для хранения информации дескриптора. Приложение явно не указать размер дескриптора не выделяют новых записей. Если приложение предоставляет сведения для записи дескриптор, номер которого выше, чем значение SQL_DESC_COUNT, драйвер автоматически увеличивается SQL_DESC_COUNT. Если приложение отменяет привязку записи дескриптора наибольший номер, драйвер автоматически уменьшается SQL_DESC_COUNT содержать количество наибольший оставшиеся присоединенной записи.
