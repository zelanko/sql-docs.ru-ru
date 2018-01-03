---
title: "Escape-последовательности, НАПРИМЕР | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a481e7dc539abc9fa206b7c1dab61de09816cd97
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="like-escape-sequence"></a>КАК Escape-последовательность
ODBC использует escape-последовательности для предложения LIKE. Ниже приведен синтаксис escape-последовательности:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Remarks  
 В форме БЭКУСА-Наура используется следующий синтаксис:  
  
 *ODBC как escape* :: =  
  
 *ODBC-esc инициатор* escape "*escape символ*" *ODBC esc признака конца.*  
  
 *escape символ* :: = *символ*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC esc признак конца* :: =}  
  
 Чтобы определить, поддерживает ли драйвер LIKE управляющие последовательности, приложение может вызвать **SQLGetInfo** с типом SQL_LIKE_ESCAPE_CLAUSE сведения.
