---
title: Метод createStatement (int, int, int) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cabeeaf2759991bda02b3dd1f59e247c7037f15
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830639"
---
# <a name="createstatement-method-int-int-int"></a>Метод createStatement (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект, который формирует [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты с заданным типом, параллелизма и возможностью сохранения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>Параметры  
 *resultSetType*  
  
 **Int** тип набора значение, представляющее результат.  
  
 *nConcur*  
  
 **Int** тип параллелизма набора значение, представляющее результат.  
  
 *nHold*  
  
 **Int** значение, представляющее возможность сохранения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект инструкции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод createStatement указывается с помощью метода createStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также  
 [Метод createStatement &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
