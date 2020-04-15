---
title: Обнаружение трубации данных позволило использовать РасширенныйAnssSL (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae1aa7a8a8b9ea2c3f3054717546506e660d5270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280704"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
Когда флаг ExtendedAnsiS'L включен и приложение вставляет данные в символ или двоичный столбец, а данные усечены, усечение будет обнаружено. При выключении флага ExtendedAnsiS'L данные усечены без предупреждения, как это было в предыдущих версиях драйверов настольной базы данных ODBC.
