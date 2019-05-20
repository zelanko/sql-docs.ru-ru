---
title: REVERSE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1ee2c26de6058e6daef58b5dbdf64ef025298bc8
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725032"
---
# <a name="reverse-ssis-expression"></a>REVERSE (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает символьное выражение в обратном порядке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, в котором требуется поменять порядок символов на обратный.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Аргумент *character_expression* должен иметь тип данных DT_WSTR.  
  
 Функция TOKEN возвращает значение NULL, если строка *character_expression* имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере используется строковый литерал. Возвращаемый результат: «ekiB niatnuoM».  
  
```  
REVERSE("Mountain Bike")  
```  
  
 В данном примере используется переменная. Если переменная **Name** содержит выражение «Touring Bike», будет возвращен результат «ekiB gniruoT».  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
