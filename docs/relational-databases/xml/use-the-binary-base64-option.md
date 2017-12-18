---
title: "Использование параметра BINARY BASE64 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c592fbb3e08fa538f669e1a72e15690962445ff
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="use-the-binary-base64-option"></a>Использование параметра BINARY BASE64
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Если в запросе задан параметр BINARY BASE64, двоичные данные возвращаются в формате кодирования base64. По умолчанию, если аргумент BINARY BASE64 не задан, режим AUTO поддерживает кодирование URL-адресов двоичных данных. Это означает, что вместо двоичных данных возвращается ссылка на относительный URL-адрес виртуального корня базы данных, в которой выполнялся запрос. Эта ссылка может использоваться для доступа к действительным двоичным данным в последующих операциях при помощи запроса объекта базы данных SQLXML ISAPI. Для идентификации изображения запрос должен предоставить достаточно данных, например первичные ключевые столбцы.  
  
 При задании запроса, если используется псевдоним для двоичного столбца представления, псевдоним возвращается в виде URL-адреса двоичных данных. В последующих операциях псевдоним не имеет смысла, и URL-адрес не может использоваться для получения изображения. Поэтому не используйте псевдонимы при запросе представления в режиме FOR XML AUTO.  
  
 Например, в запросе SELECT приведение любого столбца к большому двоичному объекту (BLOB) делает этот столбец временной сущностью, которая теряет связанные с ней имя таблицы и имя столбца. Поэтому запросы в режиме AUTO будут формировать ошибки, так как они не будут знать, куда поместить этот объект в иерархии XML. Например:  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 Следующий запрос вернет ошибку из-за приведения к типу BLOB:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 Решение этой проблемы заключается в добавлении параметра BINARY BASE64 к предложению FOR XML. Если удалено приведение типов, запрос вернет ожидаемый результат:  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 Результат:  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование режима AUTO совместно с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  
