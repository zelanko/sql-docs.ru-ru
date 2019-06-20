---
title: Использование поставщика SQLXMLOLEDB (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9801f34d1128595a2a23004327379cb213e1a0c7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62714141"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>Использование поставщика SQLXMLOLEDB (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Подразделы этого раздела содержат образцы приложений ADO, иллюстрирующих использование зависящих от поставщика SQLXMLOLEDB свойств.  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>Требования приложения для поставщика SQLXMLOLEDB версии 4.0  
 Чтобы создать рабочие образцы, использующие SQLXMLOLEDB версии 4.0, необходимо выполнить следующие действия.  
  
1.  Создать приложение Microsoft Visual Basic и добавить одну из следующих ссылок.  
  
    -   Microsoft ActiveX Data Objects 2,6 библиотеки  
  
    -   2.7 библиотеки объектов данных ActiveX  
  
    -   Библиотека объектов Microsoft ADO 2.8  
  
2.  Развернуть и установить SQLXML версии 4.0 и собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
     Дополнительные сведения см. на [основные концепции программирования на SQLXML 4.0](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md) и [Установка SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Выполнение запросов SQL &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 Демонстрирует использование свойства корневого ClientSideXML и xml для выполнения запросов SQL.  
  
 [Выполнение шаблонов, содержащих запросы SQL &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 Демонстрирует использование ClientSideXML, свойство.  
  
 [Выполнение запросов XPath &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 Демонстрирует использование свойства ClientSideXML, базовый путь и схемы сопоставления.  
  
 [Выполнение запросов XPath с пространствами имен &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 Иллюстрирует выполнение запроса к схемам пространства имен.  
  
 [Выполнение шаблонов, содержащих запросы XPath &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 Иллюстрирует выполнение шаблонов с запросами SQL с помощью свойств ClientSideXML, базовый путь и схемы сопоставления.  
  
 [Применение преобразования XSL &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 Демонстрирует использование свойств ClientSideXML и xsl в применение преобразования XSL.  
  
## <a name="see-also"></a>См. также  
 [Системные требования для SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  
