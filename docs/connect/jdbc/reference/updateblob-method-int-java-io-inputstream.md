---
title: Метод updateBlob (int, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d0263018-d326-4a7b-bf6f-5f508db899d4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 444c7f6c3f1a657ae8b5531f60359078032a7128
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787248"
---
# <a name="updateblob-method-int-javaioinputstream"></a>Метод updateBlob (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с помощью заданного входного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *inputStream*  
  
 Объект, InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBlob указывается с помощью метода updateBlob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBlob (SQLServerResultSet)](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
