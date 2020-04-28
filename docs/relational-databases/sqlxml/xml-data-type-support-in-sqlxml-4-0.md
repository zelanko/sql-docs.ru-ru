---
title: Поддержка типов данных xml в SQLXML 4.0
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4c56efd6c79b7ce7d74af621963f4b12e734d5f9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75252172"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>Поддержка типов данных xml в SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает типизированные XML-данные, используя тип данных **XML** . В этом разделе содержатся сведения о том, как SQLXML 4,0 распознает экземпляры типа данных **XML** и реализует их поддержку.  
  
## <a name="working-with-xml-data-types"></a>Работа с типами данных xml  
 Чтобы понять, как работать с таблицами SQL, которые реализуют столбцы типа данных **XML** , предоставляются следующие примеры.  
  
|Задача|Пример|Раздел|  
|----------|-------------|-----------|  
|Как сопоставлять и включать **XML-** столбцы в XML-представление|«Сопоставление XML-элемента со столбцом типа данных xml»|[Сопоставление элементов и атрибутов XSD с таблицами и столбцами по умолчанию &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Вставка данных в **XML-** столбец с помощью диаграмм обновления|«Вставка данных в столбец типа данных xml»|[Вставка данных с помощью XML диаграмм обновления &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Массовый загрузке XML-данных в **XML-** столбец|«Массовая загрузка XML-данных в столбцы типа данных xml»|[Примеры групповой загрузки XML &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Рекомендации и ограничения  
  
-   XSD: любые>не могут быть сопоставлены со столбцом, включая тип данных **XML** . ** \<** Поддержка в SQLXML для этого сценария предоставляется с помощью аннотации **SQL: overflow-поля** . Еще один обходной путь заключается в сопоставлении поля типа данных **XML** как элемента **xsd: anyType**. Этот способ показан в примере «Сопоставление XML-элемента со столбцом типа данных xml», ссылка на который дана в таблице выше.  
  
-   Запрос XPath к содержимому столбцов типа данных **XML** не поддерживается.  
  
-   Использование столбца типа данных **XML** в заметках, где они не поддерживаются (например, **SQL: relationship** и **SQL: Key-Fields**) или Allowed, приведет к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибкам, которые не будут перехвачены компонентами среднего уровня, реализующими SQLXML 4,0. Это происходит потому, что SQLXML не требуются сведения о типах SQL. Это напоминает поведение SQLXML в случае с другими типами данных, например двоичными и BLOB.  
  
-   Сопоставление **XML-** столбцов поддерживается только для схем XSD. Схемы XDR не поддерживают сопоставление **XML-** столбцов.  
  
-   При синтаксическом анализе XML SQLXML 4.0 использует поддержку, предусмотренную в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **XML-** столбец может быть либо сопоставлен как ТИПИЗИРОВАНный XML, либо как нетипизированный XML. В обоих случаях SQLXML 4.0 не проверяет входной XML.  Если входной XML недопустим или имеет неверный формат, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает об этом SQLXML и передает пользователю сведения об ошибках, возвращенные сервером.  
  
-   SQLXML 4.0 зависит от ограниченной поддержки DTD, реализованной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]позволяет использовать внутреннее определение DTD в данных типа данных **XML** , которое может использоваться для предоставления значений по умолчанию и для замены ссылок на сущности их расширенным содержимым. SQLXML передает XML-данные серверу «как есть» (в том числе внутренние DTD). Можно преобразовывать определения DTD в документы схем XML (XSD) при помощи инструментов сторонних компаний и загружать эти данные вместе со встроенными схемами XSD в базу данных.  
  
-   SQLXML 4,0 не сохраняет инструкции по обработке XML-декларации (например,) в зависимости от поведения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого XML-декларация рассматривается как директива для средства синтаксического анализа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML, и его атрибуты (версия, кодировка и автономность) теряются после преобразования данных в тип данных **XML** . Все XML-данные хранятся в кодировке UCS-2. Все остальные инструкции по обработке в экземпляре XML сохраняются; они разрешены в **XML-** столбце и могут поддерживаться SQLXML.  
  
## <a name="see-also"></a>См. также:  
 [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
