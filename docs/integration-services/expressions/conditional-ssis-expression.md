---
title: '? : (условный) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 758cd90c3932d59e725f6a8a9bf829e59ecf5474
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71290166"
---
# <a name="--conditional-ssis-expression"></a>? : (условный) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает одно из двух выражений на основе вычисления логического выражения. Если логическое выражение принимает значение TRUE, то возвращается результат вычисления первого выражения. Если логическое выражение принимает значение FALSE, возвращается результат вычисления второго выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Любое допустимое выражение, результатом которого являются TRUE, FALSE или NULL  
  
 *expression1*  
 Любое допустимое выражение.  
  
 *expression2*  
 Любое допустимое выражение.  
  
## <a name="result-types"></a>Типы результата  
 Тип данных *expression1* или *expression2*.  
  
## <a name="remarks"></a>Remarks  
 Если выражение *boolean_expression* имеет значение NULL, результат тоже будет иметь значение NULL. Если выбранное выражение, будь то *expression1* или *expression2* , принимает значение NULL, результат также примет значение NULL. Если выбранное выражение не равно NULL, а невыбранное равно NULL, результатом будет значение выбранного выражения.  
  
 Если *expression1* и *expression2* имеют одинаковый тип данных, у результата тоже будет этот тип данных. Следующие дополнительные правила применяются к типам результатов:  
  
-   Тип данных DT_TEXT требует, чтобы *expression1* и *expression2* имели одну и ту же кодовую страницу.  
  
-   Длина результата типа DT_BYTES равна длине более длинного аргумента.  
  
 Выражения *expression1* и *expression2*должны иметь допустимый тип данных и должны удовлетворять одному из приведенных ниже правил.  
  
-   **Числовой** Как *expression1* , так и *expression2* должны иметь числовой тип данных. В соответствии с правилами неявных числовых преобразований, выполняемых средством оценки выражений, пересечением типов данных должен быть числовой тип данных. NULL не может быть значением пересечения двух числовых типов данных. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
-   **Строковый** . Значения выражений *expression1* и *expression2* должны иметь строковый тип: DT_STR или DT_WSTR. Вычисленные значения этих двух выражений могут иметь различные строковые типы данных. Результат будет иметь тип данных DT_WSTR с длиной более длинного аргумента.  
  
-   **Дата, время или дата-время** . Значения выражений *expression1* и *expression2* должны иметь один из следующих типов данных: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET и DT_FILETIME.  
  
    > [!NOTE]  
    >  Система не поддерживает сравнения выражений, значения которых имеют тип данных даты, времени или даты-времени. Возникнет ошибка.  
  
     При сравнении выражений система применяет следующие правила преобразования (в порядке их перечисления).  
  
    -   Если значения двух выражений имеют один и тот же тип данных, выполняется сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIMESTAMPOFFSET, то другое будет неявно преобразовано в тип данных DT_DBTIMESTAMPOFFSET, после чего будет произведено сравнение для этого типа. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIMESTAMP2, то другое будет неявно преобразовано в тип данных DT_DBTIMESTAMP2, после чего будет произведено сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных DT_DBTIME2, то другое будет неявно преобразовано в тип данных DT_DBTIME2, после чего будет произведено сравнение для этого типа.  
  
    -   Если значение одного из выражений имеет тип данных, отличный от DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 или DT_DBTIME2, то перед началом сравнения значения будут преобразованы в тип данных DT_DBTIMESTAMP.  
  
     При сравнении выражений система исходит из следующих предположений.  
  
    -   Если оба выражения имеют тип данных, включающий доли секунды, то предполагается, что для типа, имеющего меньшее число разрядов, в недостающих разрядах содержатся нули.  
  
    -   Если оба выражения имеют тип даты, но смещение часового пояса присутствует только у одного из них, то предполагается, что дата без смещения выражена по Гринвичу (UTC).  
  
 Дополнительные сведения о типах данных см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример показывает выражение, принимающее значение `savannah` или `unknown`в зависимости от условия.  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 Этот пример показывает выражение, ссылающееся на столбец **ListPrice** . **ListPrice** имеет тип данных DT_CY. В выражении по условию происходит умножение **ListPrice** на 0,2 или 0,1.  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
