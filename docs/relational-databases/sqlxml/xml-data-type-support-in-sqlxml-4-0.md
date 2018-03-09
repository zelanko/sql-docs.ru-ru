---
title: "Поддержка типов данных в SQLXML 4.0 XML | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dfdb6b2fba95fc3e723122e9402e70caede522b1
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Поддержка типов данных xml в SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML поддерживает типизированные данные с помощью **xml** тип данных. Этот раздел содержит сведения о том, как SQLXML 4.0 распознает экземпляры **xml** тип данных и реализует их поддержку.  
  
## <a name="working-with-xml-data-types"></a>Работа с типами данных xml  
 Чтобы узнать больше о работе с таблицами SQL, которые реализуют **xml** столбцы с типами данных приведены следующие примеры:  
  
|Задача|Пример|Раздел|  
|----------|-------------|-----------|  
|Способы сопоставления и включить **xml** столбец в XML-представление|«Сопоставление XML-элемента со столбцом типа данных xml»|[По умолчанию осуществляется сопоставление элементов и атрибутов таблиц и столбцов &#40; XSD SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Вставка данных в **xml** столбца с диаграммами обновления|«Вставка данных в столбец типа данных xml»|[Вставка данных с помощью диаграмм обновления XML &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Массовой загрузке XML-данных в **xml** столбца|«Массовая загрузка XML-данных в столбцы типа данных xml»|[Примеры массовой загрузки XML &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Рекомендации и ограничения  
  
-   **\<XSD: любой >** не может быть сопоставлен столбцу, в том числе **xml** тип данных. Поддержка в SQLXML, этот сценарий обеспечивается через **SQL: Overflow-поле** заметки. Другое решение — сопоставление **xml** поле с типом данных как элемент **xsd: anyType**. Этот способ показан в примере «Сопоставление XML-элемента со столбцом типа данных xml», ссылка на который дана в таблице выше.  
  
-   Запрос XPath к содержимому **xml** столбцы типа данных не поддерживается.  
  
-   С помощью **xml** столбец типа данных в аннотациях, где не поддерживается (например, **SQL: Relationship** и **SQL: Key-поля**) или разрешается, приведет к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибки, которые не быть захвачен среднего уровня, реализующим SQLXML 4.0. Это происходит потому, что SQLXML не требуются сведения о типах SQL. Это напоминает поведение SQLXML в случае с другими типами данных, например двоичными и BLOB.  
  
-   Сопоставление **xml** столбцов поддерживается только для схемы XSD. Схемы XDR не поддерживают сопоставление **xml** столбцов.  
  
-   При синтаксическом анализе XML SQLXML 4.0 использует поддержку, предусмотренную в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Xml** столбца может быть сопоставлен либо как типизированный XML или нетипизированный XML. В обоих случаях SQLXML 4.0 не проверяет входной XML.  Если входной XML недопустим или имеет неверный формат, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает об этом SQLXML и передает пользователю сведения об ошибках, возвращенные сервером.  
  
-   SQLXML 4.0 зависит от ограниченной поддержки DTD, реализованной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать внутреннее DTD в **xml** тип данных, который может использоваться для указания значений по умолчанию и замените ссылки на сущности их развернутым содержимым. SQLXML передает XML-данные серверу «как есть» (в том числе внутренние DTD). Можно преобразовывать определения DTD в документы схем XML (XSD) при помощи инструментов сторонних компаний и загружать эти данные вместе со встроенными схемами XSD в базу данных.  
  
-   SQLXML 4.0 не сохраняет инструкции обработки декларации XML (например,) на основе режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого XML-декларация обрабатывается как директива для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксического анализа XML, а его атрибуты (версии, кодировки и автономные) теряются после данные преобразуются в **xml** тип данных. Все XML-данные хранятся в кодировке UCS-2. Все остальные инструкции по обработке в экземпляре XML сохраняются; они допустимы в **xml** столбца и могут поддерживаться SQLXML.  
  
## <a name="see-also"></a>См. также  
 [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
