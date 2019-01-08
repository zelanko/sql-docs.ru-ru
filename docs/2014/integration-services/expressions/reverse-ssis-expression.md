---
title: REVERSE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e28592369427d480fc46eb8d7e8801272a7554a2
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801736"
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
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
