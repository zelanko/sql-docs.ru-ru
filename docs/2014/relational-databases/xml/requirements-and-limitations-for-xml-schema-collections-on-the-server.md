---
title: Требования и ограничения для коллекций схем XML на сервере | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- identifiers [XML schema collections]
- XML schema collections [SQL Server], limitations
- substitution groups [XML in SQL Server]
- XML schema collections [SQL Server], guidelines
- lax validation
- enumeration facets [XML in SQL Server]
- decimal precision [XML in SQL Server]
- repeated XML schema collection values
- schema collections [SQL Server], limitations
- time zones [XML in SQL Server]
- precision decimals [XML in SQL Server]
- schema collections [SQL Server], guidelines
- lexical representation
ms.assetid: c2314fd5-4c6d-40cb-a128-07e532b40946
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 245b844872070ee16104a90ecc0734462bdad3b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63241261"
---
# <a name="requirements-and-limitations-for-xml-schema-collections-on-the-server"></a>Требования и ограничения для коллекций XML-схем на сервере
  Язык определения XML-схем (XSD) имеет некоторые ограничения при проверке правильности столбцов SQL, использующих тип данных `xml`. В следующей таблице содержатся подробные сведения об этих ограничениях и рекомендации по изменению XSD-схемы, таким образом, чтобы обеспечить возможность работы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Темы данного раздела содержат дополнительные сведения об определенных ограничениях и рекомендации по работе с ними.  
  
|Элемент|Ограничение|  
|----------|----------------|  
|**minOccurs** и **maxOccurs**|Значения атрибутов **minOccurs** и **maxOccurs** должны укладываться в 4-байтовые целые числа. Схемы, которые не соответствуют этому условию, будут отклонены сервером.|  
|**\<xsd:choice>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет схемы, содержащие примитив **\<xsd:choice>** без дочерних элементов, если только он не определен с нулевым значением атрибута **minOccurs**.|  
|**\<xsd:include>**|В настоящее время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает этот элемент. XML-схемы, содержащие данный элемент, отклоняются сервером.<br /><br /> Чтобы обойти это ограничение, можно предварительно обработать XML-схемы, содержащие директиву **\<xsd:include>** , чтобы скопировать и объединить содержимое всех включенных схем в единую схему для передачи на сервер. Дополнительные сведения см. в разделе [Предварительная обработка схемы для слияния включаемых схем](preprocess-a-schema-to-merge-included-schemas.md).|  
|**\<xsd:key>** , **\<xsd:keyref>** и **\<xsd:unique>**|В настоящее время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает эти относящиеся к XSD ограничения для обеспечения уникальности или установки ключей и ссылок на ключи. Схемы XML, содержащие эти элементы, не могут быть зарегистрированы.|  
|**\<xsd:redefine>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает этот элемент. Сведения о другом способе обновления схем см. в разделе [Элемент &#60;xsd:redefine&#62;](the-xsd-redefine-element.md).|  
|Значения **\<xsd:simpleType>**|Для простых типов, имеющих секундные компоненты, отличные от `xs:time` и `xs:dateTime`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает точность только до миллисекунд, а для компонентов `xs:time` и `xs:dateTime` — до 100 наносекунд. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] накладывает ограничения на все распознанные перечисления простых типов XSD.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает использование значения NaN в объявлениях **\<xsd:simpleType>** .<br /><br /> Дополнительные сведения см. в разделе[Значения для объявлений &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md).|  
|**xsi:schemaLocation** и **xsi:noNamespaceSchemaLocation**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пропускает эти атрибуты, если они присутствуют в данных экземпляра XML, вставленных в столбец или переменную с типом данных `xml`.|  
|**xs:QName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает типы, полученные из **xs:QName** , которые используют элемент ограничения XML-схемы.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает в качестве элемента-члена типы объединений с **xs:QName** .<br /><br /> Дополнительные сведения см. в разделе [Тип xs:QName](the-xs-qname-type.md).|  
|Добавление элементов к существующей группе замещения|Нельзя добавить элементы в существующую группу замещения в коллекции XML-схем. Группа замещения в схеме XML ограничена в том, что главный элемент и все члены этого элемента должны быть определены в одной инструкции {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Канонические формы и ограничения шаблона|Каноническое представление значения не может нарушать ограничение шаблона для своего типа. Дополнительные сведения см. в разделе [Канонические формы и ограничения шаблона](canonical-forms-and-pattern-restrictions.md).|  
|Аспекты перечисления|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает XML-схемы с типами, имеющими аспекты шаблона или перечисления, которые нарушают эти аспекты.|  
|Длина аспекта|Аспекты **length**, **minLength**и **MaxLength** хранятся в виде `long` типа. Этот тип является 32-разрядным типом. Таким образом, диапазон допустимых значений для этих значений — 2<sup>^</sup>31.|  
|Атрибут идентификатора|Каждый компонент XML-схемы может иметь атрибут ID. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает уникальность объявлений **\<xsd:attribute>** с типом **ID**, но не хранит эти значения. Областью видимости, в пределах которой значения должны быть уникальными, является инструкция {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Тип идентификатора|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает элементы типа **xs:ID**, **xs:IDREF**и **xs:IDREFS**. Схема не может объявлять элементы этого типа или элементы, полученные ограничением или расширением этого типа.|  
|Локальное пространство имен|Необходимо явно указать локальное пространство имен для элемента **\<xsd:any>** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет схемы, содержащие пустую строку ("") в качестве значения атрибута пространства имен. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует явно указать значение «##local», которое означает, что элемент без квалификатора или атрибут будет использоваться как экземпляр символа-шаблона.|  
|Смешанный тип и простое содержимое|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает ограничение смешанного типа простым содержимым. Дополнительные сведения см. в разделе [Смешанный тип и простое содержимое](mixed-type-and-simple-content.md).|  
|NOTATION, тип|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает тип NOTATION.|  
|Условия исчерпания памяти|В работе с большими коллекциями XML-схем может наступить условие исчерпания памяти. Решения этой проблемы см. в разделе [Большие коллекции XML-схем и условия нехватки памяти](large-xml-schema-collections-and-out-of-memory-conditions.md).|  
|Повторяющиеся значения|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет схемы, атрибуты block или final которых содержат повторяющиеся значения, например "restriction restriction" и "extension extension".|  
|Идентификаторы компонента схемы|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничивает идентификаторы компонентов схемы до максимальной длины в 1000 символов Юникода. Кроме того, в идентификаторах не поддерживаются суррогатные пары символов.|  
|Сведения часового пояса|В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях при проверке схемы XML сведения о часовом поясе полностью поддерживаются для значений `xs:date`, `xs:time` и `xs:dateTime`. В режиме обратной совместимости с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] сведения о часовом поясе всегда приводятся в формат UTC (время по Гринвичу). Для элементов типа `dateTime` сервер преобразует и вернет указанное время во время по Гринвичу, используя величину смещения (-05:00).|  
|Типы объединения|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает ограничения от типов объединений.|  
|Десятичные числа переменной точности|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает десятичные числа переменной точности. Тип **xs:decimal** представляет десятичные числа произвольной точности. Обработчики XML, соответствующие минимальным требованиям, должны поддерживать десятичные числа как минимум `totalDigits=18`знаков. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает количество знаков `totalDigits=38,` , но ограничивает число знаков после запятой десятью. Все экземпляры значений **xs:decimal** внутренне представляются сервером в виде числового типа SQL (38, 10).|  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Канонические формы и ограничения шаблона](canonical-forms-and-pattern-restrictions.md)|Объясняет канонические формы и ограничения шаблона.|  
|[Компоненты-шаблоны и проверка достоверности содержимого](wildcard-components-and-content-validation.md)|Описывает ограничения использования символов-шаблонов, нестрогой проверки и элементов anyType с коллекциями XML-схем.|  
|[Элемент &#60;xsd:redefine&#62;](the-xsd-redefine-element.md)|Объясняет ограничения использования элемента \<xsd:redefine> и описывает обходное решение для этой проблемы.|  
|[Тип xs:QName](the-xs-qname-type.md)|Описывает ограничение, связанное с типом xs:QName.|  
|[Значения для объявлений &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md)|Описывает ограничения, применяемые к объявлениям \<xsd:simpleType>.|  
|[Аспекты перечисления](enumeration-facets.md)|Описывает ограничение, связанное с аспектами перечислений.|  
|[Смешанный тип и простое содержимое](mixed-type-and-simple-content.md)|Описывает ограничение сужения смешанного типа до простого содержимого.|  
|[Большие коллекции схем XML и условия нехватки памяти](large-xml-schema-collections-and-out-of-memory-conditions.md)|Содержит решения проблемы с нехваткой памяти, которая может возникнуть при работе с большими коллекциями схем.|  
|[Недетерминированные модели содержимого](non-deterministic-content-models.md)|Описывает ограничения, связанные с недетерминированными моделями содержимого.|  
  
## <a name="see-also"></a>См. также:  
 [Данные XML (SQL Server)](xml-data-sql-server.md)   
 [Сравнение типизированного и нетипизированного XML](compare-typed-xml-to-untyped-xml.md)   
 [Предоставление разрешений на коллекции схем XML](grant-permissions-on-an-xml-schema-collection.md)   
 [Ограничение однозначного соответствия примитивов](unique-particle-attribution-constraint.md)   
 [Коллекции XML-схем (SQL Server)](xml-schema-collections-sql-server.md)  
  
  
