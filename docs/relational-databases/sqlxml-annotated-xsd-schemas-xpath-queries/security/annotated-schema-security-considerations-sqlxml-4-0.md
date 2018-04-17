---
title: Вопросы безопасности схем (SQLXML 4.0) с заметками | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c042438a928a1ccbbb917c210b0f24c418f5681c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Основные понятия о безопасности схемы с заметками (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Далее приводятся рекомендации по обеспечению безопасности при использовании аннотированных схем.  
  
-   Избегайте использования сопоставления по умолчанию в схемах сопоставления.  Сопоставление по умолчанию предоставляет доступ к информации о базе данных (имена таблиц и столбцов) в результирующем XML-документе, поскольку по умолчанию имена элементов сопоставляются именам таблиц, а имена атрибутов — именам столбцов. Поэтому любой пользователь, увидевший XML-документ, получает доступ к информации о таблицах и столбцах базы данных, что представляет собой потенциальную угрозу безопасности.  Чтобы избежать этого риска, в схеме следует пользоваться произвольными именами элементов и атрибутов и явным образом сопоставлять их с таблицами и столбцами с помощью заметки.  Дополнительные сведения об использовании сопоставления по умолчанию при создании схем XSD см. в разделе [по умолчанию сопоставление из элементов и атрибутов XSD с таблицами и столбцами &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Явное задание сопоставления с помощью заметок предоставляет информацию о базе данных (например, об именах таблиц и столбцов). Поэтому бывает нежелательно предоставлять публичный доступ к этим схемам.  
  
-   Некоторые запросы, например, к схеме сопоставления с рекурсией (с использованием **Максимальная глубина** заметки более высокое значение) может занять больше времени. При необходимости можно указать предел времени ожидания, задав свойство времени ожидания команды (в секундах). Например:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>См. также  
 [Схемы XSD с заметками в SQLXML 4.0](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
