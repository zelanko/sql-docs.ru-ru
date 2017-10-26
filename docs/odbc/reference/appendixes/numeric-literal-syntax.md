---
title: "Синтаксиса числовых литералов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 64a772d8a04015060aa717e4153bf6f36e5b74de
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="numeric-literal-syntax"></a>Синтаксиса числовых литералов
Для числовых литералов в ODBC используется следующий синтаксис:  
  
 *числовой литерал* :: = *подпись цифровой literal &#124; неподписанные цифровой literal*  
  
 *подпись цифровой literal* :: = [*входа*] *неподписанные цифровой literal*  
  
 *без знака цифровой literal* :: = *точного цифровой literal &#124; приблизительное цифровой literal*  
  
 *точные цифровой literal* :: = *unsigned integer* [*период*[*unsigned integer*]] *&#124; периода unsigned integer*  
  
 *знак* :: = *плюс &#124; знак «минус»*  
  
 *Приблизительное цифровой literal* :: = *показатель степени мантиссы E*  
  
 *мантисса* :: = *точного цифровой literal*  
  
 *показатель степени* :: = *подписан целое число*  
  
 *подписанные целое* :: = [*входа*] *unsigned integer*  
  
 *unsigned integer* :: = *цифрой...*  
  
 *плюс* :: =*+*  
  
 *знак «минус»* :: = -  
  
 *цифра* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0;  
  
 *период* :: =.

