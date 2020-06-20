---
title: Общие сведения об использовании запросов XPath (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a32f28268d39b0cc93a315f45d775804eacdd98
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015403"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>Основные сведения об использовании запросов XPath (SQLXML 4.0)
  Запрос на языке XPath может быть указан как часть URL-адреса или внутри шаблона. Схема сопоставления определяет структуру этого результирующего фрагмента, а значения извлекаются из базы данных. Этот процесс имеет сходные концепции с созданием представлений при помощи инструкции CREATE VIEW и написания SQL-запросов к ним.  
  
> [!NOTE]  
>  Чтобы получить представление о запросах XPath в SQLXML 4.0, необходим опыт работы с XML-представлениями и другими связанными основными понятиями — шаблонами и схемами сопоставления. Дополнительные сведения см. в статьях [Введение в схемы XSD с Заметками &#40;SQLXML 4,0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)и стандарт XPath, определенный консорциум W3C (W3C).  
  
 XML-документ состоит из узлов, таких как узел элемента, узел атрибута, текстовый узел и т. д. Например, рассмотрим следующий XML-документ:  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 В этом документе **\<Customer>** является узлом элемента, **CID** является узлом атрибута, а **"важно"** является текстовым узлом.  
  
 XPath — это язык навигации графа, используемый для выбора набора узлов из XML-документа. Каждый оператор XPath выбирает набор узлов на основе набора узлов, выбранных предыдущим оператором XPath. Например, при наличии набора **\<Customer>** узлов XPath может выбрать все **\<Order>** узлы со значением атрибута **Date** , равным **"7/14/1999"**. Результирующий набор узлов содержит все заказы с датой заказа 7/14/1999.  
  
 Язык XPath определен консорциумом W3C (World Wide Web Consortium) как стандартный язык навигации. SQLXML 4,0 реализует подмножество спецификации W3C XPath, расположенное по адресу http://www.w3.org/TR/1999/PR-xpath-19991008.html .  
  
 Далее приведены ключевые отличия реализации XPath консорциума W3C и реализации SQLXML 4.0.  
  
-   **Корневые запросы**  
  
     SQLXML 4.0 не поддерживает корневой запрос (/). Каждый запрос XPath должен начинаться на верхнем уровне **\<ElementType>** схемы.  
  
-   **Сообщения об ошибках**  
  
     Спецификация XPath консорциума W3C не определяет условия ошибки. Запросы XPath, которые не смогли выбрать какой-либо узел, возвращают пустой набор узлов. В SQLXML 4.0 запрос может вернуть несколько типов ошибок.  
  
-   **Порядок документа**  
  
     В SQLXML 4.0 порядок документа не всегда определен. Соответственно, числовые предикаты и оси, использующие порядок документа (такие, как `following`), не реализованы.  
  
     Отсутствие порядка документа также означает, что строковое значение узла может быть вычислено, только когда этот узел соответствует одному столбцу в одной строке. Элемент с дочерними элементами, или узел IDREFS, или узел NMTOKENS не могут быть преобразованы в строку.  
  
    > [!NOTE]  
    >  В некоторых случаях заметка `key-fields` или ключи заметки `relationship` могут приводить к детерминированному порядку документа. Однако это не является основным применением этих заметок для получения дополнительных сведений. см [. раздел Определение ключевых столбцов с помощью SQL: key-fields &#40;sqlxml 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) и [Указание связей с помощью sql: relationship &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).  
  
-   **Типы данных**  
  
     В SQLXML 4.0 имеются ограничения в реализации типов данных XPath `string`, `number` и `boolean`. Дополнительные сведения см. в разделе [типы данных XPath &#40;SQLXML 4,0&#41;](xpath-data-types-sqlxml-4-0.md).  
  
-   **Запросы перекрестного произведения**  
  
     SQLXML 4.0 не поддерживает запросы перекрестного произведения XPath, такие как `Customers[Order/@OrderDate=Order/@ShipDate]`. Этот запрос выбирает все наборы узлов Customer, состоящие из узлов Order, для которых OrderDate совпадает с ShipDate любого узла Order.  
  
     Однако SQLXML 4.0 не поддерживает такие запросы, как `Customer[Order[@OrderDate=@ShippedDate]]`, которые выбирают наборы узлов Customer, состоящие из узлов Order, для которых OrderDate совпадает с ShipDate.  
  
-   **Обработка ошибок и безопасность**  
  
     В зависимости от используемых схемы и выражения запроса XPath ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)] могут быть представлены пользователю при определенных условиях.  
  
 Таблицы следующего раздела содержат сведения о различиях реализации запросов XPath в SQLXML 4.0 от спецификации консорциума W3C.  
  
## <a name="supported-functionality"></a>Поддерживаемые функции  
 В следующей таблице приведены возможности языка XPath, реализованные в SQLXML 4.0.  
  
|Компонент|Item|Ссылка на образцы запросов|  
|-------------|----------|----------------------------|  
|Оси|оси `attribute`, `child`, `parent` и `self`|[Указание осей в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|Предикаты с логическими значениями, включая последовательные и вложенные предикаты.||[Указание арифметических операторов в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Все реляционные операторы|=,! =, <, \<=, > , >=|[Указание реляционных операторов в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Арифметические операторы|+, -, *, div|[Указание арифметических операторов в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Явные функции преобразования|`number()`, `string()`, `Boolean()`|[Указание явных функций преобразования в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|логические операторы|AND, OR|[Указание логических операторов в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|логические функции|`true()`, `false()`, `not()`|[Указание логических функций в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|переменные XPath||[Указание переменных XPath в запросах XPath &#40;SQLXML 4,0&#41;](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>Неподдерживаемые функциональные возможности  
 В следующей таблице приведены функции языка XPath, не реализованные в SQLXML 4.0.  
  
|Компонент|Item|  
|-------------|----------|  
|Оси|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|Предикаты с числовыми значениями||  
|Арифметические операторы|mod|  
|Функции узлов|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|Строковые функции|`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`|  
|логические функции|`lang()`|  
|Числовые функции|`sum()`, `floor()`, `ceiling()`, `round()`|  
|Оператор Union|&#124;|  
  
 При указании запросов XPath в шаблоне обратите внимание на следующее поведение.  
  
-   XPath может содержать такие символы, как < или &, которые имеют особые значения в XML (а шаблон — это XML-документ). Эти символы необходимо отформатировать с помощью & кодировки XML или указать XPath в URL-адресе.  
  
## <a name="see-also"></a>См. также:  
 [Использование запросов XPath в SQLXML 4.0](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
