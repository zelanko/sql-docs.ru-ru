---
title: Поддержка FOR XML для строковых типов данных | Документация Майкрософт
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
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f44b0158e539d91cba8bfe03587eaf63800c9d9d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190348"
---
# <a name="for-xml-support-for-string-data-types"></a>Поддержка FOR XML для строковых типов данных
  Пробельные символы XML-кода, формируемого инструкцией FOR XML, преобразуются в сущности.  
  
 В следующем примере создается образец таблицы **T** , в который вставляются данные, содержащие символы перевода строки, возврата каретки и табуляции. Инструкция SELECT получает данные из таблицы.  
  
```  
CREATE TABLE T  
(  
  c1 int identity primary key,  
  c2 varchar(100)  
);  
go  
  
INSERT T (c2) VALUES ('Special character 0xD for carriage return ' + convert(varchar(10), 0xD) + ' after carriage return');  
INSERT T (c2) VALUES ('Special character 0x9 for tab ' + convert(varchar(10), 0x9) + ' after tab' );  
INSERT T (c2) VALUES ('Special character 0xA for line feed ' + convert(varchar(10), 0xA) + ' after line feed');  
go  
SELECT *   
FROM T  
FOR XML AUTO;  
go  
```  
  
 Результат:  
  
```  
 <T c1="1" c2="Special character 0xD for carriage return   
 after carriage return" />  
 <T c1="2" c2="Special character 0x9 for tab     after tab" />  
 <T c1="3" c2="Special character 0xA for line feed   
after line feed" />  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Символ возврата каретки в первой строке представлен в виде сущности &#xD.  
  
-   Символ табуляции во второй строке представлен в виде сущности &#x09.  
  
-   Символ перевода строки в третьей строке представлен в виде сущности &#xA.  
  
## <a name="see-also"></a>См. также  
 [Поддержка FOR XML для различных типов данных SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  