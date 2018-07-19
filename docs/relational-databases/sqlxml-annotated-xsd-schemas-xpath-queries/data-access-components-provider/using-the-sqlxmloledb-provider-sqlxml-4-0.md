---
title: Использование поставщика SQLXMLOLEDB (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e2c9d60c84cde37eeef80dd5c916544a0ca83e6f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38053812"
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
  
  
