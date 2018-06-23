---
title: TOKENCOUNT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a592523c4df67ce1ee74985e0927106cc60cf251
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102463"
---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT (выражение служб SSIS)
  Возвращает несколько токенов в строке, в которой они разделены указанными символами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Строка, содержащая токены, разделенные соответствующими символами.  
  
 *delimiter_string*  
 Строка, содержащая символы разделения. Например, строка «; ,» содержит три символа разделения: точку с запятой, пробел и запятую.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Примечания  
 Следующие примечания относятся к функции TOKEN.  
  
-   Строка разделения может содержать один или несколько символов разделения.  
  
-   Первые разделители пропускаются.  
  
-   TOKENCOUNT работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции TOKEN. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR.  
  
-   Функция TOKENCOUNT возвращает результат 0 (нуль), если строка character_expression имеет значение NULL.  
  
-   Переменные и столбцы могут использоваться в качестве аргументов для этого выражения.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем примере функция TOKENCOUNT возвращает значение 3, потому что строка содержит 3 маркера: "01", "12", "2011".  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 В следующем примере функция TOKENCOUNT возвращает 4 потому, что в строке 4 токена («a», «little», «white», «dog»).  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 В следующем примере функция TOKENCOUNT возвращает значение 1. Функция выполняет синтаксический анализ входной строки на предмет разделителей, и, поскольку их в строке нет, добавляет всю строку как первый токен.  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 В следующем примере функция TOKENCOUNT возвращает значение 4. Строка разделителя в этом примере содержит 5 разделителей. Входная строка содержит 4 маркера: "a", "little", "white", "dog".  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 В следующем примере функция TOKENCOUNT возвращает значение 4. Функция пропускает все пробелы в начале строки.  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  