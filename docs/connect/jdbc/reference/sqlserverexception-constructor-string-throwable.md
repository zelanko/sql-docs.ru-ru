---
title: Конструктор SQLServerException (java.lang.String, java.lang.Throwable) | Документация Майкрософт
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
ms.openlocfilehash: 14984450507b5eea63d2fbe88bb2e7f957f61868
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971077"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangthrowable"></a>Конструктор SQLServerException (java.lang.String, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) по полученным объектам **string** и **throwable**.

## <a name="syntax"></a>Синтаксис  
  
```  
public SQLServerException(java.lang.String errText,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Параметры  
 *errText*  
  
 Строка, содержащая текст ошибки.
 
 *cause*  
  
 Объект с атрибутом throwable, который содержит причину исключения.
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Класс SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
