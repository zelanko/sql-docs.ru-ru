---
title: Метод getAsciiStream (SQLServerClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4dfd2c53ab5fb883edbaabbc33c8ac8255b284ed
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799985"
---
# <a name="getasciistream-method-sqlserverclob"></a>Метод getAsciiStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Материализует объект CLOB в виде потока ASCII.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Входной поток, содержащий данные объекта CLOB.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getAsciiStream указывается с помощью метода getAsciiStream в интерфейсе java.sql.Clob.  
  
 Всегда возвращает поток байтов и предполагает, что данные в объекте CLOB имеют формат ASCII, поскольку нет возможности узнать, что данные используют Юникод или другую многобайтовую кодировку страницы.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
