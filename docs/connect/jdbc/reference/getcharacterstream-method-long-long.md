---
title: Метод getCharacterStream (длинный, длинный) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a47b7ea56873b0b502ba39a91e4d1ba30044e993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953259"
---
# <a name="getcharacterstream-method-long-long"></a>Метод getCharacterStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает данные **Clob** в виде объекта Reader или потока символов с указанной позицией и длиной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Значение **long**, определяющее смещение до первого символа извлекаемого фрагмента значения.  
  
 *length*  
  
 Значение **long**, определяющее длину в символах для извлекаемого фрагмента значения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader, содержащий данные **Clob**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCharacterStream задается методом getCharacterStream в интерфейсе Java. SQL. CLOB.  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream (SQLServerClob)](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
