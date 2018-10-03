---
title: С заметками о безопасности схемы (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b46c996c7b89be06558d3ad4b43e1c1bca6aa370
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162330"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Основные понятия о безопасности схемы с заметками (SQLXML 4.0)
  Далее приводятся рекомендации по обеспечению безопасности при использовании аннотированных схем.  
  
-   Избегайте использования сопоставления по умолчанию в схемах сопоставления.  Сопоставление по умолчанию предоставляет доступ к информации о базе данных (имена таблиц и столбцов) в результирующем XML-документе, поскольку по умолчанию имена элементов сопоставляются именам таблиц, а имена атрибутов — именам столбцов. Поэтому любой пользователь, увидевший XML-документ, получает доступ к информации о таблицах и столбцах базы данных, что представляет собой потенциальную угрозу безопасности.  Чтобы избежать этого риска, в схеме следует пользоваться произвольными именами элементов и атрибутов и явным образом сопоставлять их с таблицами и столбцами с помощью заметки.  Дополнительные сведения об использовании сопоставления по умолчанию, при создании схем XSD см. в разделе [по умолчанию сопоставление из элементов и атрибутов XSD с таблицами и столбцами &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Явное задание сопоставления с помощью заметок предоставляет информацию о базе данных (например, об именах таблиц и столбцов). Поэтому бывает нежелательно предоставлять публичный доступ к этим схемам.  
  
-   Некоторые запросы (например, запросы к схеме сопоставления с рекурсией, заданные с помощью заметки `max-depth` с высоким значением) могут выполняться довольно долго. При необходимости можно указать предел времени ожидания, задав свойство время ожидания команды (в секундах). Пример:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>См. также  
 [Схемы XSD с заметками в SQLXML 4.0](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
