---
title: Метод createStatement (int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: df361da2387a053b9550c4b4e25dc94cced6579b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800638"
---
# <a name="createstatement-method-int-int"></a>Метод createStatement (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), который создает объекты [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) с заданным типом и видом параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Параметры  
 *resultSetType*  
  
 Значение типа **int**, представляющее тип результирующего набора.  
  
 *resultSetConcurrency*  
  
 Значение типа **int**, представляющее тип параллелизма результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект инструкции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createStatement указывается с помощью метода createStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод createStatement (SQLServerConnection)](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
