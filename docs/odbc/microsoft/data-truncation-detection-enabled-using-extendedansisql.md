---
title: Определение усечения данных с помощью ExtendedAnsiSQL | Документы Microsoft
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
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8f50d96ea39ab5b9d2b23af2318f1dee724c04a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включить с помощью ExtendedAnsiSQL определение усечения данных
Если включен флаг ExtendedAnsiSQL и приложение осуществляет вставку данных в char или двоичного столбца, данные будут усечены, будет обнаружен усечение. При отключении флаг ExtendedAnsiSQL данные усекаются без предупреждения, как это было в предыдущих версиях драйверов ODBC системной базы данных.
