---
title: Метод getCharacterStream () (SQLServerNClob) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 4cf25f858e740dcb8ec9d10467808bcd619aec46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801782"
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
 Объект Reader, содержащий данные **NCLOB**.  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCharacterStream указывается с помощью метода getCharacterStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream (SQLServerNClob)](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
