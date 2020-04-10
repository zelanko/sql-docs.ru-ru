---
title: Конструктор SQLServerException (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 95217b384788ea78bd389948930ba34f580036ec
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902620"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>Конструктор SQLServerException (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) по полученному значению **объекта**, объектам **string**, **string**, **StreamError** и значению **boolean**.

## <a name="syntax"></a>Синтаксис  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            StreamError streamError,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Параметры  
 *obj*  
  
 Буфер ввода-вывода, создавший исключение.

 *errText*  
  
 Строка, содержащая текст ошибки.
  
 *sqlState*  
  
 Объект перечисления, который содержит состояние SQL.
 
 *streamError*  
  
 Объект StreamError, который содержит сведения об ошибке.
 
 *bStack*  
  
 Логическое значение, которое указывает, нужно ли создавать трассировку стека.
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Класс SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
