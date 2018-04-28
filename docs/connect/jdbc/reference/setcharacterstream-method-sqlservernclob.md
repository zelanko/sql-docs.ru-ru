---
title: Метод setCharacterStream (SQLServerNClob) | Документы Microsoft
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
ms.topic: article
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f938c4d404c448a0001c462feeec5151f5ab9b69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setcharacterstream-method-sqlservernclob"></a>Метод setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает поток, используемый для записи поток символов Юникода, **NCLOB** этим **java.sql.NClob** представляет, начиная с указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция, с которой начинается запись **NCLOB** value; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Можно создать объект модуля записи, который представляет поток, к которому символы в кодировке Юникод.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setCharacterStream указывается с помощью метода setCharacterStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
