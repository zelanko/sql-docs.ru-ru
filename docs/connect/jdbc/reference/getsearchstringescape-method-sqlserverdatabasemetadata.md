---
title: Метод getSearchStringEscape (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a12b9ca70dd8e48fa92df9b1b2be55b22ee6994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721362"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Метод getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение **String**, которое можно использовать для избежания подстановочных знаков.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее убираемый подстановочный знак строки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSearchStringEscape указывается с помощью метода getSearchStringEscape в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод используется только для поиска по шаблону в метаданных. Он возвращает символ \\. В шаблоне поиска **String** можно убирать подстановочные знаки ("%" и "_"), добавляя перед ними обратную косую черту, и передавать их в виде литералов. "\\%" преобразуется в "[%]", а "\\\_" — в "[\_]".  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
