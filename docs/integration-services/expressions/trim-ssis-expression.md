---
title: TRIM (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 8a6b946110049321c50427e33fbca05876ec6384
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297348"
---
# <a name="trim-ssis-expression"></a>TRIM (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
## <a name="see-also"></a>См. также:  
 [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
