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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 517c21f7b64fa7ceb662af9839a9fed1a1e6eff6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304925"
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
