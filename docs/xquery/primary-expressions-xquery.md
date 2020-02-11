---
title: Первичные выражения (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3504b4f04b1b9842f786eeef3ecf1f105563f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74200515"
---
# <a name="primary-expressions-xquery"></a>Первичные выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Первичные выражения XQuery включают литералы, ссылки на переменные, выражения элементов контекста, конструкторы и вызовы функций.  
  
## <a name="literals"></a>Литералы  
 Литералы выражений XQuery могут быть строковыми или числовыми. Строковый литерал может содержать стандартные ссылки на сущности, которые являются последовательностью символов. Последовательность начинается с амперсанда, представляющего отдельный символ, который в других случаях может иметь синтаксическую значимость. Далее приводятся стандартные ссылки на сущности в выражениях XQuery.  
  
|Ссылка на сущность|Представляет|  
|----------------------|----------------|  
|`&lt;`|\<|  
|`&gt;`|>|  
|`&amp;`|&|  
|`&quot;`|"|  
|`&apos;`|'|  
  
 Строковый литерал также может содержать символьную ссылку, XML-ссылку на символ Юникода, определяемую десятичным или шестнадцатеричным элементом кода. Например, символ евро может быть представлен ссылкой на символ "&\#8364;".  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует XML версии 1.0 в качестве основы при синтаксическом анализе.  
  
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
SELECT @var.query(' <SalaryRange>Salary &gt; 50000 and &lt; 100000</SalaryRange>')  
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
  
 Встроенные логические функции ( **true ()** и **false ())** могут использоваться для представления логических значений, как показано в следующем примере.  
  
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
DECLARE namespace x="https://X";  
for $x:i in /root return data($x:i)')  
GO  
```  
  
 Для ссылки на переменные SQL можно использовать функцию расширения SQL: variable (), как показано в следующем запросе.  
  
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
  
-   Объявления внешних переменных не поддерживаются. Решением этой проблемы является использование [функции SQL: variable ()](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="context-item-expressions"></a>Выражения элементов контекста  
 Элементом контекста является элемент, обрабатываемый в текущем контексте выражения пути. Он инициализируется в экземпляре типа XML-данных, значение которого не равно NULL, с помощью узла документов. Его также можно изменить с помощью метода nodes () в контексте выражений XPath или предикатов [].  
  
 Элемент контекста возвращается выражением, содержащим точку (.). Например, следующий запрос оценивает каждый элемент <`a`> для наличия атрибута. `attr` Если этот атрибут присутствует, элемент возвращается. Следует отметить, что условие в предикате требует, чтобы контекстный узел определялся одной точкой.  
  
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
 Можно вызывать встроенные функции XQuery и функции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SQL: variable () и SQL: column (). Список реализованных функций см. в разделе [функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md).  
  
#### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения реализации.  
  
-   Объявление функций в прологе XQuery не поддерживается.  
  
-   Импорт функций не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Создание XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)
 
