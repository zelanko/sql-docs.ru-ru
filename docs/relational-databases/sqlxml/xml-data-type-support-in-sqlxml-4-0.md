---
title: Поддержка типов данных в SQLXML 4.0 XML | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8bb3b7a7f5acfdea3f38af731a0a8d2eec86bdf9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085707"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Поддержка типов данных xml в SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML поддерживает типизированные данные с помощью **xml** тип данных. Этот раздел содержит сведения о том, как SQLXML 4.0 распознает экземпляры **xml** тип данных и реализует их поддержку.  
  
## <a name="working-with-xml-data-types"></a>Работа с типами данных xml  
 Чтобы узнать больше о работе с таблицами SQL, которые реализуют **xml** столбцы, с типом данных приведены следующие примеры:  
  
|Задача|Пример|Раздел|  
|----------|-------------|-----------|  
|Как сопоставить и включать **xml** столбца в XML-представление|«Сопоставление XML-элемента со столбцом типа данных xml»|[По умолчанию осуществляется сопоставление элементов и атрибутов с таблицами и столбцами XSD &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Вставка данных в **xml** столбцов с диаграммами обновления|«Вставка данных в столбец типа данных xml»|[Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Массовая загрузка XML-данных в **xml** столбца|«Массовая загрузка XML-данных в столбцы типа данных xml»|[Примеры массовой загрузки XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Рекомендации и ограничения  
  
-   **\<XSD: любой >** не может быть сопоставлен столбец, в том числе **xml** тип данных. Поддержка в SQLXML, этот сценарий предоставляется через **SQL: Overflow-поле** заметки. Другим обходным методом является сопоставление **xml** поля с типом данных как элемент **xsd: anyType**. Этот способ показан в примере «Сопоставление XML-элемента со столбцом типа данных xml», ссылка на который дана в таблице выше.  
  
-   Запрос XPath к содержимому **xml** столбцы типа данных не поддерживается.  
  
-   С помощью **xml** столбец типа данных в заметках, где не поддерживается (такие как **SQL: Relationship** и **SQL: Key-поля**) или разрешается, приведет к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибки, которые будут не будет перехватить в приложении среднего уровня, реализующим SQLXML 4.0. Это происходит потому, что SQLXML не требуются сведения о типах SQL. Это напоминает поведение SQLXML в случае с другими типами данных, например двоичными и BLOB.  
  
-   Сопоставление **xml** столбцы поддерживается только для схемы XSD. Схемы XDR не поддерживают сопоставление **xml** столбцов.  
  
-   При синтаксическом анализе XML SQLXML 4.0 использует поддержку, предусмотренную в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Xml** столбца может быть сопоставлен либо как типизированный XML или нетипизированный XML. В обоих случаях SQLXML 4.0 не проверяет входной XML.  Если входной XML недопустим или имеет неверный формат, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает об этом SQLXML и передает пользователю сведения об ошибках, возвращенные сервером.  
  
-   SQLXML 4.0 зависит от ограниченной поддержки DTD, реализованной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать внутреннее DTD в **xml** типа данных, которые можно использовать для предоставления значений по умолчанию и заменить ссылки на сущности их расширенным содержимым. SQLXML передает XML-данные серверу «как есть» (в том числе внутренние DTD). Можно преобразовывать определения DTD в документы схем XML (XSD) при помощи инструментов сторонних компаний и загружать эти данные вместе со встроенными схемами XSD в базу данных.  
  
-   SQLXML 4.0 не сохраняет инструкции обработки декларации XML (например,) на основе режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого XML-декларация обрабатывается как директива для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство синтаксического анализа XML и его атрибуты (версии, кодировки и автономный) будут утеряны, после преобразования данных для **xml** тип данных. Все XML-данные хранятся в кодировке UCS-2. Все остальные инструкции по обработке в экземпляре XML сохраняются; они допускаются в **xml** столбца и могут поддерживаться SQLXML.  
  
## <a name="see-also"></a>См. также  
 [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
