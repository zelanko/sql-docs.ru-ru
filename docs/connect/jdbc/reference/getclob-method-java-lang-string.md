---
title: Метод getClob (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ad871d09-ec43-4885-9067-20854b439b0c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9ba397d39378e6e45bf63dffa4eb2efbca3b432c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67953027"
---
# <a name="getclob-method-javalangstring"></a>Метод getClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение заданного параметра большого двоичного объекта JDBC в виде объекта Clob на языке программирования Java по заданному имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Clob getClob(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Clob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getClob определен с помощью метода getClob в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getClob (SQLServerCallableStatement)](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
