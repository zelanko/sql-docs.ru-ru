---
title: Метод modify() (тип данных xml) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5c98ef9c726d2db5b5ec06d71a00de08288098a0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68051282"
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
  
  
