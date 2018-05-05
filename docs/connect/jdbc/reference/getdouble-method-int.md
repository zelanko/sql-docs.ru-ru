---
title: Метод getDouble (int) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDouble (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c0ed63bb-5ebe-4155-9f91-8fbfeac9c3b2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90d101350ef6b9722285eddf3d2f584d671ac9c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getdouble-method-int"></a>Метод getDouble (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде **двойные** на Java по заданному индексу параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public double getDouble(int index)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **двойные** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getDouble указывается с помощью getDouble метода в интерфейсе java.sql.CallableStatement.  
  
 Этот метод возвращает все типы числовых данных с помощью Java **двойные** точность.  
  
## <a name="see-also"></a>См. также  
 [Метод getDouble &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
