---
title: Общие сведения об использовании запросов XPath (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c8edb6cb54d2ef600080093729a9ff0c06f4082
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671643"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>Основные сведения об использовании запросов XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Запрос на языке XPath может быть указан как часть URL-адреса или внутри шаблона. Схема сопоставления определяет структуру этого результирующего фрагмента, а значения извлекаются из базы данных. Этот процесс имеет сходные концепции с созданием представлений при помощи инструкции CREATE VIEW и написания SQL-запросов к ним.  
  
> [!NOTE]  
>  Чтобы получить представление о запросах XPath в SQLXML 4.0, необходим опыт работы с XML-представлениями и другими связанными основными понятиями — шаблонами и схемами сопоставления. Дополнительные сведения см. в разделе [введение в схемы XSD с заметками &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)и в стандарте XPath определен консорциумом World Wide Web Consortium (W3C).  
  
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
  
 В этом документе  **\<клиента >** является узлом элемента **cid** — это узел атрибута и **«Важное»** является текстовым узлом.  
  
 XPath — это язык навигации графа, используемый для выбора набора узлов из XML-документа. Каждый оператор XPath выбирает набор узлов на основе набора узлов, выбранных предыдущим оператором XPath. Например, имея набор  **\<клиента >** узлов, XPath может выбрать все  **\<порядок >** узлов с **даты** значениеатрибута **«7/14/1999»**. Результирующий набор узлов содержит все заказы с датой заказа 7/14/1999.  
  
 Язык XPath определен консорциумом W3C (World Wide Web Consortium) как стандартный язык навигации. SQLXML 4.0 реализует часть спецификации XPath консорциума W3C, которая находится в каталоге https://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 Далее приведены ключевые отличия реализации XPath консорциума W3C и реализации SQLXML 4.0.  
  
-   **Корневые запросы**  
  
     SQLXML 4.0 не поддерживает корневой запрос (/). Каждый запрос XPath должен начинать с высшего уровня  **\<ElementType >** в схеме.  
  
-   **Отчет об ошибках**  
  
     Спецификация XPath консорциума W3C не определяет условия ошибки. Запросы XPath, которые не смогли выбрать какой-либо узел, возвращают пустой набор узлов. В SQLXML 4.0 запрос может вернуть несколько типов ошибок.  
  
-   **Порядок документа**  
  
     В SQLXML 4.0 порядок документа не всегда определен. Таким образом, числовые предикаты и оси, использующие порядок документа (такие как **следующие**), не реализованы.  
  
     Отсутствие порядка документа также означает, что строковое значение узла может быть вычислено, только когда этот узел соответствует одному столбцу в одной строке. Элемент с дочерними элементами, или узел IDREFS, или узел NMTOKENS не могут быть преобразованы в строку.  
  
    > [!NOTE]  
    >  В некоторых случаях **полей ключей** заметки или ключи из **связь** заметка может привести к детерминированному порядку документа. Тем не менее, это не Главная цель этих заметок, Дополнительные сведения, см. в разделе [идентификации ключевых столбцов с использованием SQL: Key-поля &#40;SQLXML 4.0&#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) и [указание связей с помощью sql: связь &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).  
  
-   **Типы данных**  
  
     SQLXML 4.0 имеются ограничения в реализации XPath **строка**, **номер**, и **логическое** типов данных. Дополнительные сведения см. в разделе [типов данных XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).  
  
-   **Запросы перекрестного произведения**  
  
     SQLXML 4.0 не поддерживает запросы перекрестного произведения XPath, такие как `Customers[Order/@OrderDate=Order/@ShipDate]`. Этот запрос выбирает все наборы узлов Customer, состоящие из узлов Order, для которых OrderDate совпадает с ShipDate любого узла Order.  
  
     Однако SQLXML 4.0 не поддерживает такие запросы, как `Customer[Order[@OrderDate=@ShippedDate]]`, которые выбирают наборы узлов Customer, состоящие из узлов Order, для которых OrderDate совпадает с ShipDate.  
  
-   **Обработка ошибок и безопасность**  
  
     В зависимости от используемых схемы и выражения запроса XPath ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)] могут быть представлены пользователю при определенных условиях.  
  
 Таблицы следующего раздела содержат сведения о различиях реализации запросов XPath в SQLXML 4.0 от спецификации консорциума W3C.  
  
## <a name="supported-functionality"></a>Поддерживаемые функции  
 В следующей таблице приведены возможности языка XPath, реализованные в SQLXML 4.0.  
  
|Компонент|Элемент|Ссылка на образцы запросов|  
|-------------|----------|----------------------------|  
|Оси|**атрибут**, **дочерних**, **родительского**, и **self** осей|[Указание осей в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|Предикаты с логическими значениями, включая последовательные и вложенные предикаты.||[Задание арифметических операторов в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Все реляционные операторы|=, !=, <, \<=, >, >=|[Указание реляционных операторов в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|арифметические операторы;|+, -, *, div|[Задание арифметических операторов в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Явные функции преобразования|**Number()**, **string()**, **Boolean()**|[Определение явных функций преобразования в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|логические операторы|AND, OR|[Указание логических операторов в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|логические функции|**true()**, **false()**, **not()**|[Указание логических функций в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|переменные XPath||[Указание переменных XPath в запросах XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>Неподдерживаемая функциональность  
 В следующей таблице приведены функции языка XPath, не реализованные в SQLXML 4.0.  
  
|Компонент|Элемент|  
|-------------|----------|  
|Оси|**предок**, **предка or-self**, **потомков**, **descendant-or-self (/ /)**, **следующие**,  **следующий одноуровневый**, **пространства имен**, **выше**, **предыдущему**|  
|Предикаты с числовыми значениями||  
|арифметические операторы;|mod|  
|Функции узлов|**предок**, **предка or-self**, **потомков**, **descendant-or-self (/ /)**, **следующие**,  **следующий одноуровневый**, **пространства имен**, **выше**, **предыдущему**|  
|Строковые функции|**String()**, **concat()**, **starts-with()**, **contains()**, **substring-before()**,  **SUBSTRING-AFTER()**, **substring()**, **string-length() языка**, **normalize()**, **translate()**|  
|логические функции|**lang()**|  
|Числовые функции|**SUM()**, **floor()**, **ceiling()**, **round()**|  
|Оператор Union|&#124;|  
  
 При указании запросов XPath в шаблоне обратите внимание на следующее поведение.  
  
-   XPath может содержать символы, такие как < or &, которые имеют особые значения в XML (и шаблон является XML-документом). При использовании &-кодировки XML необходимо экранировать эти символы или указывать XPath в URL-адресе.  
  
## <a name="see-also"></a>См. также  
 [Использование запросов XPath в SQLXML 4.0](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
  
  
