---
title: "Управляющие последовательности интервала | Документы Microsoft"
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
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9be0ccc925003985c9c680d3107029a929403643
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="interval-escape-sequences"></a>Управляющие последовательности интервала
ODBC использует escape-последовательности для литералов интервал. Ниже приведен синтаксис escape-последовательности:  
  
 {*интервал литерал*}  
  
 Синтаксис BNF *интервал литерал*, см. [синтаксис интервале](../../../odbc/reference/appendixes/interval-literal-syntax.md) далее в этом приложении.  
  
 Интервал литерала escape-последовательность поддерживается в том случае, если типы данных интервала поддерживаются источником данных. Приложение должно вызывать **SQLGetTypeInfo** , чтобы определить, поддерживаются ли эти типы данных.
