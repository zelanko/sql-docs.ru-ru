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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188801"
---
# <a name="like-escape-sequence"></a>Escape-последовательность LIKE
ODBC использует escape-последовательности для предложения LIKE. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *ODBC-like-escape* ::=  
  
 *ODBC-esc инициатор* escape "*escape-символ*" *ODBC esc признак конца.*  
  
 *escape-character* ::= *character*  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 Чтобы определить, поддерживает ли драйвер LIKE escape последовательности, приложение может вызвать **SQLGetInfo** с типом SQL_LIKE_ESCAPE_CLAUSE сведения.
