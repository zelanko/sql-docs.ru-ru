---
title: Escape-последовательность LIKE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65447904f32b7e0457ed807f18e942b334ddc236
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626622"
---
# <a name="like-escape-sequence"></a>Escape-последовательность LIKE
ODBC использует escape-последовательности для предложения LIKE. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *Like-escape-последовательность ODBC* :: =  
  
 *ODBC-esc инициатор* escape "*escape-символ*" *ODBC esc признак конца.*  
  
 *escape-символ* :: = *символ*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC-esc-признак конца* :: =}  
  
 Чтобы определить, поддерживает ли драйвер LIKE escape последовательности, приложение может вызвать **SQLGetInfo** с типом SQL_LIKE_ESCAPE_CLAUSE сведения.
