---
title: "Функция SOUNDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SOUNDEX
- SOUNDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SOUNDEX function
- comparing string data
- strings [SQL Server], similarity
- strings [SQL Server], comparing
- SOUNDEX values
ms.assetid: 8f1ed34e-8467-4512-a211-e0f43dee6584
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ec170c756fd207c648e210de15df9d18024ea718
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="soundex-transact-sql"></a>SOUNDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает четырехсимвольный код (SOUNDEX) для оценки степени сходства двух строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SOUNDEX ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Алфавитно-цифровое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar**  
  
## <a name="remarks"></a>Замечания  
 Функция SOUNDEX преобразует алфавитно-цифровую строку в 4-символьный код, чье значение зависит от способа звучания строки при произношении. Первый символ кода является первым символом *character_expression*, преобразованным в верхний регистр. Второй, третий и четвертый символы кода являются числами, которые обозначают буквы в выражении. Буквы A, E, I, O, U, H, W и Y игнорируются, если только не являются первой буквой строки. Нули добавляются в конце при необходимости производить четырехсимвольный код. Дополнительные сведения о коде SOUNDEX см. в разделе [система индексирования Soundex](https://www.archives.gov/research/census/soundex.html).  
  
 Коды SOUNDEX из разных строк можно сравнивать, чтобы узнать, насколько похоже звучат строки при произношении. Функция DIFFERENCE выполняет SOUNDEX по двум строкам и возвращает целое число, представляющее сходство кодов SOUNDEX для этих строк.  
  
 Функция SOUNDEX учитывает параметры сортировки. Строковые функции могут быть вложенными.  
  
## <a name="soundex-compatibility"></a>Совместимость SOUNDEX  
 В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в функции SOUNDEX использовалось подмножество правил SOUNDEX. При уровне совместимости базы данных, равном 110 или выше, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет более полный набор правил.  
  
 После обновления до уровня совместимости 110 или выше, может потребоваться перестроить индексы, кучи или ограничения CHECK, которые используется функция SOUNDEX.  
  
-   Кучу, которая содержит материализованный вычисляемый столбец, определенный функцией SOUNDEX, нельзя запрашивать, пока она не будет перестроена с помощью инструкции `ALTER TABLE <table> REBUILD`.  
  
-   При повышении уровня совместимости ограничения CHECK, определенные функцией SOUNDEX, отключаются. Чтобы включить ограничение, выполните инструкцию `ALTER TABLE <table> WITH CHECK CHECK CONSTRAINT ALL`.  
  
-   Запросы к индексам (в том числе индексированным представлениям), которые содержат материализованный вычисляемый столбец, определенный функцией SOUNDEX, можно выполнять только после их перестроения с помощью инструкции `ALTER INDEX ALL ON <object> REBUILD`.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование функции SOUNDEX и связанной с ней функции DIFFERENCE. В первом примере стандартные значения `SOUNDEX` возвращаются для всех согласных. Возвращение функции `SOUNDEX` для `Smith` и `Smythe` выдает одинаковый результат SOUNDEX, поскольку все гласные, буквы `y` и `h`, а также удвоенные буквы не включаются.  
  
```  
-- Using SOUNDEX  
SELECT SOUNDEX ('Smith'), SOUNDEX ('Smythe');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
  
----- -----   
S530  S530    
  
(1 row(s) affected)  
```  
  
 Функция `DIFFERENCE` производит сравнение результатов шаблонов `SOUNDEX`. В следующем примере показаны две строки, различающиеся только по гласной. Возвращенное значение `4` означает максимальное сходство.  
  
```  
-- Using DIFFERENCE  
SELECT DIFFERENCE('Smithers', 'Smythers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
-----------   
4             
  
(1 row(s) affected)  
```  
  
 В следующем примере строки различаются в согласных, следовательно, возвращенное значение `2` указывает на большую степень различия.  
  
```  
SELECT DIFFERENCE('Anothers', 'Brothers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
-----------   
2             
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример демонстрирует использование функции SOUNDEX и связанной с ней функции DIFFERENCE. В первом примере стандартные значения `SOUNDEX` возвращаются для всех согласных. Возвращение функции `SOUNDEX` для `Smith` и `Smythe` выдает одинаковый результат SOUNDEX, поскольку все гласные, буквы `y` и `h`, а также удвоенные буквы не включаются.  
  
```  
-- Using SOUNDEX  
SELECT SOUNDEX ('Smith'), SOUNDEX ('Smythe');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
  
----- -----   
S530  S530    
  
(1 row(s) affected)  
```  
  
 Функция `DIFFERENCE` производит сравнение результатов шаблонов `SOUNDEX`. В следующем примере показаны две строки, различающиеся только по гласной. Возвращенное значение `4` означает максимальное сходство.  
  
```  
-- Using DIFFERENCE  
SELECT DIFFERENCE('Smithers', 'Smythers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
-----------   
4             
  
(1 row(s) affected)  
```  
  
 В следующем примере строки различаются в согласных, следовательно, возвращенное значение `2` указывает на большую степень различия.  
  
```  
SELECT DIFFERENCE('Anothers', 'Brothers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Допустимо для параметров сортировки Latin1_General.  
  
```  
-----------   
2             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Разница & #40; Transact-SQL & #41;](../../t-sql/functions/difference-transact-sql.md)   
 [Строковые функции & #40; Transact-SQL & #41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  


