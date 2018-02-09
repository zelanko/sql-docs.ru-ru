---
title: "Первичные выражения (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- variable references [XQuery]
- primary expressions [XQuery]
- function calls [XQuery]
- expressions [XQuery], primary
- literals [XQuery]
- context item expressions [XQuery]
ms.assetid: d4183c3e-12b5-4ca0-8413-edb0230cb159
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 339cb237a14869c2d747d81e32bc572ba003a5e3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="primary-expressions-xquery"></a>Первичные выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Первичные выражения XQuery включают литералы, ссылки на переменные, выражения элементов контекста, конструкторы и вызовы функций.  
  
## <a name="literals"></a>Литералы  
 Литералы выражений XQuery могут быть строковыми или числовыми. Строковый литерал может содержать стандартные ссылки на сущности, которые являются последовательностью символов. Последовательность начинается с амперсанда, представляющего отдельный символ, который в других случаях может иметь синтаксическую значимость. Далее приводятся стандартные ссылки на сущности в выражениях XQuery.  
  
|Ссылка на сущность|Представляет|  
|----------------------|----------------|  
|&lt;|\<|  
|&gt;|>|  
|&amp;|&|  
|&quot;|"|  
|&apos;|'|  
  
 Строковый литерал также может содержать символьную ссылку, XML-ссылку на символ Юникода, определяемую десятичным или шестнадцатеричным элементом кода. Например, знак евро может быть представлена символьной ссылкой «&\#8364;».  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует XML версии 1.0 в качестве основы для синтаксического анализа.  
  
### <a name="examples"></a>Примеры  
 Следующие примеры иллюстрируют применение литералов, а также ссылок на сущности и символы.  
  
 Этот код возвращает ошибку, поскольку символы `<'` и `'>` имеют специальное значение:  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <SalaryRange>Salary > 50000 and < 100000</SalaryRange>')  
GO  
```  
  
 При использовании вместо них ссылки на сущность запрос выполняется.  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <SalaryRange>Salary > 50000 and < 100000</SalaryRange>')  
GO  
```  
  
 Следующий пример иллюстрирует использование символьной ссылки для представления знака евро:  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <a>€12.50</a>')  
```  
  
 Результат.  
  
 `<a>€12.50</a>`  
  
 В следующем примере разделителями в запросе являются апострофы. Таким образом, апостроф в строковом значении представляется двумя последовательными апострофами.  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query('<a>I don''t know</a>')  
Go  
```  
  
 Результат.  
  
 `<a>I don't know</a>`  
  
 Встроенные логические функции **true()** и **false()**, может использоваться для представления логических значений, как показано в следующем примере.  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query('<a>{true()}</a>')  
GO  
```  
  
 Конструктор прямых элементов задает выражение в фигурных скобках. Оно заменяется своим значением в итоговом XML-файле.  
  
 Результат.  
  
 `<a>true</a>`  
  
## <a name="variable-references"></a>Ссылки на переменные  
 Ссылка на переменную в выражении XQuery — это QName, перед которым ставится знак $. В данной реализации поддерживаются только ссылки на переменные без префиксов. Например, следующий запрос задает переменную `$i` в выражении FLWOR.  
  
```  
DECLARE @var XML  
SET @var = '<root>1</root>'  
SELECT @var.query('  
 for $i in /root return data($i)')  
GO  
```  
  
 Следующий запрос не выполнится, поскольку в имя переменной добавлен префикс пространства имен.  
  
```  
DECLARE @var XML  
SET @var = '<root>1</root>'  
SELECT @var.query('  
DECLARE namespace x="http://X";  
for $x:i in /root return data($x:i)')  
GO  
```  
  
 Ссылки на переменные SQL можно использовать функции SQL: variable() расширения, как показано в следующем запросе.  
  
```  
DECLARE @price money  
SET @price=2500  
DECLARE @x xml  
SET @x = ''  
SELECT @x.query('<value>{sql:variable("@price") }</value>')  
```  
  
 Результат.  
  
 `<value>2500</value>`  
  
#### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения реализации.  
  
-   Переменные с префиксами пространства имен не поддерживаются.  
  
-   Импорт модулей не поддерживается.  
  
-   Объявления внешних переменных не поддерживаются. Решением является использование [функции SQL: variable()](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="context-item-expressions"></a>Выражения элементов контекста  
 Элементом контекста является элемент, обрабатываемый в текущем контексте выражения пути. Он инициализируется в экземпляре типа XML-данных, значение которого не равно NULL, с помощью узла документов. Его можно изменить с помощью метода nodes(), в контексте выражений XPath или предикатов [].  
  
 Элемент контекста возвращается выражением, содержащим точку (.). Например, следующий запрос проверяет каждый элемент <`a`> на наличие атрибута `attr`. Если этот атрибут присутствует, элемент возвращается. Следует отметить, что условие в предикате требует, чтобы контекстный узел определялся одной точкой.  
  
```  
DECLARE @var XML  
SET @var = '<ROOT>  
<a>1</a>  
<a attr="1">2</a>  
</ROOT>'  
SELECT @var.query('/ROOT[1]/a[./@attr]')  
```  
  
 Результат.  
  
 `<a attr="1">2</a>`  
  
## <a name="function-calls"></a>Вызовы функций  
 Может вызывать встроенные функции XQuery и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] функции SQL: variable() и SQL: column(). Список реализованных функций см. в разделе [функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md).  
  
#### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения реализации.  
  
-   Объявление функций в прологе XQuery не поддерживается.  
  
-   Импорт функций не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Построение XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  
