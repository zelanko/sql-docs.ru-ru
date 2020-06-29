---
title: TRIM (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 756d9bd066f4ecbcb1cfb7e43cec8ca7ea2713a6
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437071"
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
  
## <a name="remarks"></a>Remarks  
 Функция TRIM возвращает результат NULL, если аргумент имеет значение NULL.  
  
 Функция TRIM работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции TRIM. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере удаляются начальные и конечные пробелы из строкового литерала. Возвращаемый результат — «New York».  
  
```  
TRIM("   New York   ")  
```  
  
 Данный пример удаляет начальные и конечные пробелы из результата сцепления столбцов **FirstName** и **LastName** . Пустая строка между столбцами **FirstName** и **LastName** не удалена.  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a>См. также:  
 [LTRIM (выражение служб SSIS)](trim-ssis-expression.md)   
 [RTRIM (выражение служб SSIS)](rtrim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
