---
title: "Метод Modify() (тип данных xml) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81838bf62f9b2c92dce4df8a167785fdfbf7abb2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="modify-method-xml-data-type"></a>Метод modify() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет содержимое XML-документа. Этот метод используется для изменения содержимого **xml** переменной или столбце типа. Этот метод использует DML-инструкцию языка XML для вставки, обновления и удаления узлов из данных XML. **Modify()** метод **xml** тип данных может использоваться только в предложении SET инструкции UPDATE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Аргументы  
 XML_DML  
 Строка языка обработки данных для XML. Обновление XML-документа выполняется в соответствии с этим выражением.  
  
> [!NOTE]  
>  Если возвращается сообщение об ошибке **modify()** метод будет вызван на значение null или значение null.  
  
## <a name="examples"></a>Примеры  
 Поскольку **modify()** требует строку в XML языка обработки данных (DML), образцы для **modify()** содержатся в разделах, описывающих DML-инструкции. Эти примеры см. в разделе [Вставить &#40; Язык XML DML &#41; ](../../t-sql/xml/insert-xml-dml.md), [удалить &#40; Язык XML DML &#41; ](../../t-sql/xml/delete-xml-dml.md) и [замените значение &#40; Язык XML DML &#41; ](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

