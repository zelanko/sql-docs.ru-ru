---
title: Метод position (byte, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e6056412f6ab2726112d5286f2f52c83ff6691cf
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802468"
---
# <a name="position-method-byte-long"></a>Метод position (byte, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает положение указанного шаблона в BLOB-объекте по заданному **байту** шаблона массива и начального индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *bPattern*  
  
 Шаблон для поиска.  
  
 *start*  
  
 Индекс, с которого начинается поиск.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **long**, указывающее позицию, в которой обнаружен шаблон, или значение "-1", если шаблон не обнаружен.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод позиция указывается с помощью метода положение в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Метод Position &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
