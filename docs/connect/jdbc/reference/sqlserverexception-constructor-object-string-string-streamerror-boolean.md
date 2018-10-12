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
manager: craigg
ms.openlocfilehash: 89d156ca5024ed49cbc3b5256266c393c897ae12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756392"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>Конструктор SQLServerException (java.lang.Object, java.lang.String, java.lang.String, StreamError, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) Получив **объект**, **строка** объекта, **строка** объект,  **StreamError** объекта и **логическое**.

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
  
 Буфер ввода-ВЫВОДА, сформировавшего исключение.

 *errText*  
  
 Строка, содержащая текст ошибки.
  
 *sqlState*  
  
 Объект перечисления, содержащий сведения о состоянии SQL.
 
 *streamError*  
  
 Объект StreamError, содержащий сведения об ошибке.
 
 *bStack*  
  
 Логическое значение, указывающее следует ли формировать трассировку стека.
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Класс SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
