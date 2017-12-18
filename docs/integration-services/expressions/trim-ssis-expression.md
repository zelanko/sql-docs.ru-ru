---
title: "TRIM (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 48ed42d0e12ed6b3d80c61a392b50a529813899e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="trim-ssis-expression"></a>TRIM (выражение служб SSIS)
  Возвращает символьное выражение после удаления начальных и конечных пробелов.  
  
> [!NOTE]  
>  Функция TRIM не удаляет символы-разделители, такие как знаки табуляции или перевода строки. Юникод обеспечивает элементы кода для множества различных типов пробелов, однако данная функция распознает только элемент кода 0x0020 в Юникоде. Если строки двухбайтовой кодировки (DBCS) преобразованы в Юникод, они могут включать пробелы, отличные от 0x0020. Тогда функция не в состоянии удалить такие пробелы. Чтобы удалить все типы пробелов, можно использовать метод обрезки Microsoft Visual Basic .NET в скрипте, запускаемом из компонента скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого удаляются пробелы.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Замечания  
 Функция TRIM возвращает результат NULL, если аргумент имеет значение NULL.  
  
 Функция TRIM работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции TRIM. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере удаляются начальные и конечные пробелы из строкового литерала. Возвращаемый результат — «New York».  
  
```  
TRIM("   New York   ")  
```  
  
 Данный пример удаляет начальные и конечные пробелы из результата сцепления столбцов **FirstName** и **LastName** . Пустая строка между столбцами **FirstName** и **LastName** не удалена.  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a>См. также  
 [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
