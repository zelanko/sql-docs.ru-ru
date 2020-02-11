---
title: Error (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 91d07c6bbb4eb4731c9a802e47cd8f4c71aa5aeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68031236"
---
# <a name="error-mdx"></a>Error (многомерные выражения)


  Вызывает ошибку, при необходимости выводя заданное сообщение об ошибке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Error_Text*  
 Допустимое строковое сообщение, содержащее сообщение об ошибке.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано, как использовать функцию **Error** внутри вычисляемой меры.  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
