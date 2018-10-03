---
title: Управляющие последовательности интервала | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81481db74d973da0e54bc6bf9e70550fa3cc0c81
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767822"
---
# <a name="interval-escape-sequences"></a>Escape-последовательности интервалов
ODBC использует escape-последовательности для литералов интервала. Синтаксис escape-последовательность выглядит следующим образом:  
  
 {*литерал интервала*}  
  
 Для синтаксиса BNF *литерал интервала*, см. в разделе [синтаксис литерала интервала](../../../odbc/reference/appendixes/interval-literal-syntax.md) далее в этом приложении.  
  
 Литерал escape-последовательность интервал поддерживается в том случае, если типы данных интервала поддерживаются источником данных. Приложение должно вызывать **SQLGetTypeInfo** чтобы определить, поддерживаются ли эти типы данных.
