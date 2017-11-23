---
title: "Определение усечения данных с помощью ExtendedAnsiSQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2704dac2cd6b3a64becf5592d082a0635243153c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включить с помощью ExtendedAnsiSQL определение усечения данных
Если включен флаг ExtendedAnsiSQL и приложение осуществляет вставку данных в char или двоичного столбца, данные будут усечены, будет обнаружен усечение. При отключении флаг ExtendedAnsiSQL данные усекаются без предупреждения, как это было в предыдущих версиях драйверов ODBC системной базы данных.
