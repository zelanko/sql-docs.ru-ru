---
title: Использование параметра BINARY BASE64 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5c934556e1b402de4ecd013bf821c17fdd36b4b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096592"
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
  
## <a name="see-also"></a>См. также  
 [Использование режима AUTO совместно с FOR XML](use-auto-mode-with-for-xml.md)  
  
  