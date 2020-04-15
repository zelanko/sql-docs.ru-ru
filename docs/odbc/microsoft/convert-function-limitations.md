---
title: Ограничения функции CONVERT Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, CONVERT function limitations
- Convert function limitations [ODBC]
ms.assetid: 3c81fc58-57f0-4dd7-be16-2b146eb15cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63f4258e737327ae11f03a96cfef3cdecf133e53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281034"
---
# <a name="convert-function-limitations"></a>Ограничения функции CONVERT
Сбои преобразования типа приводят к тому, что пострадавший столбец устанавливается в NULL.  
  
 Ни тип данных DATE, ни TIMESTAMP не могут быть преобразованы в другой тип данных (или сам) функцией CONVERT.
