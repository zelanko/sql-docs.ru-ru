---
title: RTRIM (выражение служб SSIS) | Документы Майкрософт
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
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5dbed13c23ab6f1b72aea0dd9c21018e282a0fee
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329148"
---
# <a name="rtrim-ssis-expression"></a>RTRIM (выражение служб SSIS)
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
  
  
