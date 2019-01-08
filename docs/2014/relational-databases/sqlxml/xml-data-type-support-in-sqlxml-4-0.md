---
title: Поддержка типов данных в SQLXML 4.0 XML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1a0fa49a1dac16ed366c66c72f7d800ccc4aed8e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750626"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Поддержка типов данных xml в SQLXML 4.0
  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML поддерживает типизированные данные с помощью `xml` тип данных. В этом разделе представлены сведения о том, как SQLXML 4.0 распознает экземпляры типов данных `xml` и реализует их поддержку.  
  
## <a name="working-with-xml-data-types"></a>Работа с типами данных xml  
 Следующие примеры представлены для более глубокого понимания работы с таблицами SQL, реализующими столбцы с типами данных `xml`.  
  
|Задача|Пример|Раздел|  
|----------|-------------|-----------|  
|Сопоставление столбца `xml` и его включение в XML-представление|«Сопоставление XML-элемента со столбцом типа данных xml»|[По умолчанию осуществляется сопоставление элементов и атрибутов с таблицами и столбцами XSD &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Вставка данных в столбец `xml` с диаграммами обновления|«Вставка данных в столбец типа данных xml»|[Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Массовая загрузка XML-данных в столбец `xml`|«Массовая загрузка XML-данных в столбцы типа данных xml»|[Примеры массовой загрузки XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Рекомендации и ограничения  
  
-   **\<XSD: любой >** не может быть сопоставлен столбец, в том числе `xml` тип данных. В SQLXML это делается с помощью заметки `sql:overflow-field`. Другой способ обойти это ограничение — сопоставление поля с типом данных `xml` в качестве элемента `xsd:anyType`. Этот способ показан в примере «Сопоставление XML-элемента со столбцом типа данных xml», ссылка на который дана в таблице выше.  
  
-   Запрос XPath к содержимому столбца с типом данных `xml` не поддерживается.  
  
-   Использование столбца `xml` в заметках, где он не поддерживается (например, `sql:relationship` и `sql:key-fields`) или не разрешается, приведет к ошибкам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые невозможно будет перехватить в приложении среднего уровня, реализующим SQLXML 4.0. Это происходит потому, что SQLXML не требуются сведения о типах SQL. Это напоминает поведение SQLXML в случае с другими типами данных, например двоичными и BLOB.  
  
-   Сопоставление столбцов `xml` поддерживается только для схем XSD. Схемы XDR не поддерживают сопоставление столбцов `xml`.  
  
-   При синтаксическом анализе XML SQLXML 4.0 использует поддержку, предусмотренную в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Столбец `xml` может быть сопоставлен либо как типизированный, либо как нетипизированный XML. В обоих случаях SQLXML 4.0 не проверяет входной XML.  Если входной XML недопустим или имеет неверный формат, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает об этом SQLXML и передает пользователю сведения об ошибках, возвращенные сервером.  
  
-   SQLXML 4.0 зависит от ограниченной поддержки DTD, реализованной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать внутреннее DTD в типе данных `xml`, с помощью которого можно определять значения по умолчанию и заменять ссылки на сущности их развернутым содержимым. SQLXML передает XML-данные серверу «как есть» (в том числе внутренние DTD). Можно преобразовывать определения DTD в документы схем XML (XSD) при помощи инструментов сторонних компаний и загружать эти данные вместе со встроенными схемами XSD в базу данных.  
  
-   SQLXML 4.0 не сохраняет инструкции обработки декларации XML (например,) на основе режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого XML-декларация рассматривается как директива синтаксическому анализатору XML [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а его атрибуты (версия, кодировка и автономность) после преобразования данных в тип `xml` будут потеряны. Все XML-данные хранятся в кодировке UCS-2. Все остальные инструкции по обработке в экземпляре XML сохраняются, они допустимы в столбцах `xml` и могут поддерживаться SQLXML.  
  
## <a name="see-also"></a>См. также  
 [Данные XML (SQL Server)](../xml/xml-data-sql-server.md)  
  
  
