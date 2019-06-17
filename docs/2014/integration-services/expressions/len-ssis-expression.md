---
title: LEN (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a8bcaeb04bdc2ff8b37860ffc434d2e188436411
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769080"
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
  
## <a name="remarks"></a>Примечания  
 Аргумент *character_expression* может иметь следующий тип данных: DT_WSTR, DT_TEXT, DT_NTEXT или DT_IMAGE. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 Если параметр *character_expression* является строковым литералом либо столбцом данных типа DT_STR, перед выполнением функции LEN он автоматически приводится к типу DT_WSTR. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделе [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
