---
title: "Метод modify() (тип данных xml) | Документы Майкрософт"
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 429797447e56ecb57f0dc257bfd13bea59ea1f40
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="modify-method-xml-data-type"></a>Метод modify() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет содержимое XML-документа. Данный метод служит для изменения содержимого переменной или столбца типа **xml**. Этот метод использует DML-инструкцию языка XML для вставки, обновления и удаления узлов из данных XML. Метод **modify()** типа данных **xml** может быть использован только в предложении SET инструкции UPDATE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Аргументы  
 XML_DML  
 Строка языка обработки данных для XML. Обновление XML-документа выполняется в соответствии с этим выражением.  
  
> [!NOTE]  
>  Возвращается ошибка, если метод **modify()** вызван при значении NULL или приводит к значению NULL.  
  
## <a name="examples"></a>Примеры  
 Поскольку метод **modify()** требует строку на XML-языке обработки данных (DML), образцы для метода **modify()** содержатся в разделах, описывающих DML-инструкции. Эти примеры см. в разделах [insert (XML DML)](../../t-sql/xml/insert-xml-dml.md), [delete (XML DML)](../../t-sql/xml/delete-xml-dml.md) и [replace value of (XML DML)](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
