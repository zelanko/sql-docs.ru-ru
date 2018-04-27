---
title: LEN (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31ae12cd8c17a436a4d5f8e023ea6efeda8a0898
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="len-ssis-expression"></a>LEN (выражение служб SSIS)
  Возвращает число символов в символьном выражении. Функция учитывает начальные и завершающие пробелы, содержащиеся в строке. Результат выполнения функции LEN одинаков для строк из одно- и двухбайтовых символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Вычисляемое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Аргумент *character_expression* может иметь следующий тип данных: DT_WSTR, DT_TEXT, DT_NTEXT или DT_IMAGE. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Если параметр *character_expression* является строковым литералом либо столбцом данных типа DT_STR, перед выполнением функции LEN он автоматически приводится к типу DT_WSTR. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделе [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Если функции LEN подается аргумент, имеющий тип данных BLOB, например DT_TEXT, DT_NTEXT или DT_IMAGE, результатом ее выполнения будет размер входного объекта в байтах.  
  
 Функция LEN возвращает значение NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере функция возвращает длину строкового литерала. Возвращается значение 12.  
  
```  
LEN("Ball Bearing")  
```  
  
 В данном примере функция возвращает разницу между длиной значений в столбцах **FirstName** и **LastName** .  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 Возвращает длину имени компьютера, хранящегося в системной переменной **MachineName**.  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
