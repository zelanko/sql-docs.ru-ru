---
title: Интервал Побег Последовательности (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304959"
---
# <a name="interval-escape-sequences"></a>Escape-последовательности интервалов
ODBC использует последовательности побега для интервала буквальных. Синтаксис этой последовательности побега заключается в следующем:  
  
 -*интервал-буквальный*  
  
 Для синтаксиса BNF *интервального буквального*, [см. Раздел Интервал Литературный синтаксис](../../../odbc/reference/appendixes/interval-literal-syntax.md) позже в этом приложении.  
  
 Последовательность интервала буквального побега поддерживается, если типы данных интервала поддерживаются источником данных. Для определения того, поддерживаются ли эти типы данных, приложение должно позвонить в **s'LGetTypeInfo.**
