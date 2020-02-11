---
title: КАК escape-последовательность | Документация Майкрософт
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
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041712"
---
# <a name="like-escape-sequence"></a>Escape-последовательность LIKE
ODBC использует escape-последовательности для предложения LIKE. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Remarks  
 В нотации BNF синтаксис выглядит следующим образом:  
  
 *ODBC-Like-escape* :: =  
  
 *ODBC-ESC-* Escape-*символ*"управляющая последовательность" *ODBC-ESC-признак конца*  
  
 *escape-символ* :: = *символ*  
  
 *ODBC-ESC-инициатор* :: = {  
  
 *ODBC-ESC-признак конца* :: =}  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательность LIKE, приложение может вызвать **SQLGetInfo** с типом сведений SQL_LIKE_ESCAPE_CLAUSE.
