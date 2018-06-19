---
title: REVERSE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f5d213179d88a70c2f02436e5b1d0b1f2674bce4
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406706"
---
# <a name="reverse-ssis-expression"></a>REVERSE (выражение служб SSIS)
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
  
  
