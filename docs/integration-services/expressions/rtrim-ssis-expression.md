---
title: RTRIM (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c58da8b33c431f62f4567379beca8b5b12beea4f
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914950"
---
# <a name="rtrim-ssis-expression"></a>RTRIM (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Возвращает символьное выражение после удаления конечных пробелов.  
  
> [!NOTE]  
>  RTRIM не удаляет пробельные символы, такие как символы табуляции и символы перехода на новую строку. Юникод обеспечивает элементы кода для множества различных типов пробелов, однако данная функция распознает только элемент кода 0x0020 в Юникоде. Если строки двухбайтовой кодировки (DBCS) преобразованы в Юникод, они могут включать пробелы, отличные от 0x0020. Тогда функция не в состоянии удалить такие пробелы. Для удаления всех видов пробелов можно использовать метод Microsoft Visual Basic .NET RTrim в скрипте, выполняемом из компонента скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого удаляются пробелы.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Метод RTRIM работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции RTRIM. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Метод RTRIM возвращает значение NULL, если значением аргумента является NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере удаляются конечные пробелы из строкового литерала. Возвращаемый результат — «Hello».  
  
```  
RTRIM("Hello   ")  
```  
  
 В этом примере удаляются конечные пробелы из объединения столбцов **FirstName** и **LastName** .  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 В этом примере удаляются конечные пробелы из переменной **FirstName** .  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>См. также:  
 [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
