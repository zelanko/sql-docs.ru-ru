---
title: REPLACE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c2750412c9024263f4e576a883a23b4ffb430924
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188421"
---
# <a name="replace-ssis-expression"></a>REPLACE (выражение служб SSIS)
  Возвращает символьное выражение после замены символьной строки в выражении другой символьной строкой или пустой строкой.  
  
> [!NOTE]  
>  Функция REPLACE часто использует длинные строки. Последствия усечения могут быть корректно обработаны или могут вызвать предупреждение или ошибку. Дополнительные сведения см. в разделе [Синтаксис (службы SSIS)](syntax-ssis.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Допустимое символьное выражение, в котором будет выполняться поиск.  
  
 *searchstring*  
 Допустимое символьное выражение, которое функция пытается найти.  
  
 *replacementstring*  
 Допустимое символьное выражение, являющееся строкой замены.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Примечания  
 Длина *searchstring* должна быть больше нуля.  
  
 Длина *replacementstring* может быть нулевой.  
  
 Аргументы *searchstring* и *replacementstring* могут использовать переменные и столбцы.  
  
 Функция REPLАCE работает только с типом данных DT_WSTR. Аргументы*character_expression1, character_expression2* и *character_expression3* , которые являются строковыми литералами или столбцами данных, содержащими данные типа DT_STR, неявно приводятся к типу данных DT_WSTR до того, как функция REPLACE выполнит свою операцию. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделе [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Функция REPLACE возвращает NULL, если значение любого из аргументов равно NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере используется строковый литерал. Результат — «All Terrain Bike».  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 Этот пример удаляет строку «Bike» из столбца **Product** .  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 Этот пример заменяет значения в столбце **DaysToManufacture** . Эта столбец содержит целочисленный тип данных, а выражение включает приведение значений столбца **DaysToManufacture** к типу данных DT_WSTR.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>См. также  
 [Подстрока &#40;выражение служб SSIS&#41;](substring-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
