---
title: "REPLACE (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 93f62c9307e149e2bfcae74282c1bd6b0e6f9ea4
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="replace-ssis-expression"></a>REPLACE (выражение служб SSIS)
  Возвращает символьное выражение после замены символьной строки в выражении другой символьной строкой или пустой строкой.  
  
> [!NOTE]  
>  Функция REPLACE часто использует длинные строки. Последствия усечения могут быть корректно обработаны или могут вызвать предупреждение или ошибку. Дополнительные сведения см. в разделе [Синтаксис (службы SSIS)](../../integration-services/expressions/syntax-ssis.md).  
  
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
  
## <a name="remarks"></a>Remarks  
 Длина *searchstring* должна быть больше нуля.  
  
 Длина *replacementstring* может быть нулевой.  
  
 Аргументы *searchstring* и *replacementstring* могут использовать переменные и столбцы.  
  
 Функция REPLАCE работает только с типом данных DT_WSTR. Аргументы*character_expression1, character_expression2* и *character_expression3* , которые являются строковыми литералами или столбцами данных, содержащими данные типа DT_STR, неявно приводятся к типу данных DT_WSTR до того, как функция REPLACE выполнит свою операцию. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделе [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [SUBSTRING (выражение служб SSIS)](../../integration-services/expressions/substring-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
