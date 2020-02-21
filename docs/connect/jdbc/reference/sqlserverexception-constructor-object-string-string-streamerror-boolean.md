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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c1cc42a09e455fa42d3f89b05903a22afc945424
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971122"
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
  
  
