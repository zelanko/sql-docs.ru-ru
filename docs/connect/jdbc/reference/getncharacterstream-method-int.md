---
title: Метод getNCharacterStream (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6ae704f5-823c-4dfe-8c08-07b547c61a3c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 21cfd942fe43dedcbe19e8d0fe88a831bae76872
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784595"
---
# <a name="getncharacterstream-method-int"></a>Метод getNCharacterStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение указанного параметра в виде объекта Reader по индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.io.Reader getNCharacterStream(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 AReaderobject.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод следует использовать при доступе к **NCHAR**, **NVARCHAR** и **LONGNVARCHAR** параметров.  
  
 Этот метод getNCharacterStream указывается с помощью метода getNCharacterStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNCharacterStream (SQLServerCallableStatement)](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
