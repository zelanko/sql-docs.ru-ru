---
title: Поддержка FOR XML для строковых типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 48a6063193b0ad629316bb1a7d6180c27178561b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076684"
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
  
  
