---
title: Управляющие последовательности интервала | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3973a5149aa5861b2d194cd4487a15b0f97e7f94
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907629"
---
# <a name="interval-escape-sequences"></a>Управляющие последовательности интервала
ODBC использует escape-последовательности для литералов интервал. Ниже приведен синтаксис escape-последовательности:  
  
 {*интервал литерал*}  
  
 Синтаксис BNF *интервал литерал*, см. [синтаксис интервале](../../../odbc/reference/appendixes/interval-literal-syntax.md) далее в этом приложении.  
  
 Интервал литерала escape-последовательность поддерживается в том случае, если типы данных интервала поддерживаются источником данных. Приложение должно вызывать **SQLGetTypeInfo** , чтобы определить, поддерживаются ли эти типы данных.
