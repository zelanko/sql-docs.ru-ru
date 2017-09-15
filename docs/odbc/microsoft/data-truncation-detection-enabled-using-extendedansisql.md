---
title: "Определение усечения данных с помощью ExtendedAnsiSQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 87affbd567a817ea119c405b64f96effe2358052
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включить с помощью ExtendedAnsiSQL определение усечения данных
Если включен флаг ExtendedAnsiSQL и приложение осуществляет вставку данных в char или двоичного столбца, данные будут усечены, будет обнаружен усечение. При отключении флаг ExtendedAnsiSQL данные усекаются без предупреждения, как это было в предыдущих версиях драйверов ODBC системной базы данных.
