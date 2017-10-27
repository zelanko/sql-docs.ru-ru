---
title: "Использование параметра BINARY BASE64 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a0cfc14849df2f82429b00e8d912ceba6c74200e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="use-the-binary-base64-option"></a>Использование параметра BINARY BASE64
  Если в запросе задан аргумент BINARY BASE64, двоичные данные возвращаются в формате кодирования base64. По умолчанию, если аргумент BINARY BASE64 не задан, режим AUTO поддерживает кодирование URL-адресов двоичных данных. Это означает, что вместо двоичных данных возвращается ссылка на относительный URL-адрес виртуального корня базы данных, в которой выполнялся запрос. Эта ссылка может использоваться для доступа к действительным двоичным данным в последующих операциях при помощи запроса объекта базы данных SQLXML ISAPI. Для идентификации изображения запрос должен предоставить достаточно данных, например первичные ключевые столбцы.  
  
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
  
  

