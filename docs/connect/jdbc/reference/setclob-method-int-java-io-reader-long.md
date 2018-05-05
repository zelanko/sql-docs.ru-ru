---
title: Метод setClob (int, java.io.Reader, long) | Документы Microsoft
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
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 144c7c466da82ecd4e09b1bb9b9540560d437652
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setclob-method-int-javaioreader-long"></a>Метод setClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект чтения, который находится на заданное число знаков.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** , указывающее индекс параметра.  
  
 *Модуль чтения*  
  
 Объект модуля чтения.  
  
 *длина*  
  
 Объект **длинные** указывает число символов в значении параметра.  
  
## <a name="remarks"></a>Замечания  
 Этот метод setClob указывается с помощью метода setClob в интерфейсе java.sql.PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>См. также  
 [Метод setClob &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
