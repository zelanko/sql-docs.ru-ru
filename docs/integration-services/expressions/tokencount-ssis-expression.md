---
title: TOKENCOUNT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 508f752b04307e8930b19f0175608667c5ef1d90
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788542"
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
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
