---
title: Метод getCharacterStream () в SQLServerNClob | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7641698e-b25c-4bb2-bcc7-9273bdd08bf0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e6ce2f52a8f3326a753d1647bd865c7d6d939e45
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803417"
---
# <a name="getcharacterstream-method--sqlservernclob"></a>Метод getCharacterStream () (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает данные **NCLOB** в виде объекта **Reader** или потока символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader, содержащий данные **NCLOB**.  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCharacterStream указывается с помощью метода getCharacterStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream (SQLServerNClob)](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
