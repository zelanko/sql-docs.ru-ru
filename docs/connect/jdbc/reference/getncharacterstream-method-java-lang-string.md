---
title: Метод getNCharacterStream (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 45d2695b-0727-419d-8921-a51d6feef0aa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cc5e5e72c4b1aedcc9e10ef74ff2946f2fb2d588
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981622"
---
# <a name="getncharacterstream-method-javalangstring"></a>Метод getNCharacterStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение указанного параметра в виде объекта Reader по имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.io.Reader getNCharacterStream(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод должен использоваться при доступе к параметрам **NCHAR**, **NVARCHAR** и **LONGNVARCHAR**.  
  
 Этот метод getNCharacterStream задается с помощью метода getNCharacterStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNCharacterStream (SQLServerCallableStatement)](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
