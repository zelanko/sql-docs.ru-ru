---
title: Метод createStatement (int, int) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e260135aa251012edfa98a08d4db3c358c17c51
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927667"
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
 Объект оператора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createStatement указывается с помощью метода createStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод createStatement (SQLServerConnection)](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
