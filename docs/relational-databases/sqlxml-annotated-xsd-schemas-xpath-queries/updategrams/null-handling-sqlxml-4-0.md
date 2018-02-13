---
title: "(SQLXML 4.0) обработкой значений NULL | Документы Microsoft"
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
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e5b4f5ceaa6ba03a48f834d0ad4ec26baf029a6
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="null-handling-sqlxml-40"></a>Обработка значений NULL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Синтаксис XML определяет значение NULL как отсутствие. (Например, если значение атрибута или элемента равно NULL, считается, что он отсутствует в XML-документе.) В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, **updg: nullValue** атрибут позволяет задать значение NULL в качестве значения элемента или атрибута.  
  
 Например, следующая диаграмма обновления гарантирует, что **заголовок** для контакта с **ContactID** 64 имеет значение NULL, а затем обновляет **заголовок** значение на «Mr.» для этого контакта.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Когда параметры передаются диаграмме обновления, значение NULL может передаваться как значение параметра. Это делается путем указания **nullvalue** атрибута в  **\<updg:header >** блока. Пример см. в разделе [передача параметров в диаграммах обновления &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
