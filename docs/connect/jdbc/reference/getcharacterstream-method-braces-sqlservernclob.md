---
title: Метод getCharacterStream () (SQLServerNClob) | Документы Microsoft
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
ms.assetid: 7641698e-b25c-4bb2-bcc7-9273bdd08bf0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 165a559f20693b9ba4b35b255ed69bcc01504183
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getcharacterstream-method--sqlservernclob"></a>Метод getCharacterStream () (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает **NCLOB** данные в виде **чтения** объекта или потока символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект чтения, который содержит **NCLOB** данных.  
  
## <a name="remarks"></a>Замечания  
 Этот метод getCharacterStream указывается с помощью метода getCharacterStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также  
 [Метод getCharacterStream &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
