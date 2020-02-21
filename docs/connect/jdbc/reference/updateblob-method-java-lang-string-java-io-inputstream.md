---
title: Метод updateBlob (java.lang.String, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 018cd71b-4b58-49a7-990e-d28dbb12da70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23eaa798e05ae9653695cc33753e14cb57b72c61
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67997108"
---
# <a name="updateblob-method-javalangstring-javaioinputstream"></a>Метод updateBlob (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с помощью заданного входного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *inputStream*  
  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBlob определен с помощью метода updateBlob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBlob (SQLServerResultSet)](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
