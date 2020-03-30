---
title: Метод setNClob (int, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dae9fbeb16a5b9c9c881e4250206b7f83344ef78
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973797"
---
# <a name="setnclob-method-int-javaioreader-long"></a>Метод setNClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру значение указанного объекта Reader, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *reader*  
  
 Объект Reader, указывающий значение параметра.  
  
 *length*  
  
 Значение **long**, указывающее количество символов в значении параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setNClob определен с помощью метода setNClob в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNClob (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
