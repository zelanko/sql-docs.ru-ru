---
title: Метод getCharacterStream (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0dd69211302a10fe72fc2742cbcd8b6bda7c933
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68213698"
---
# <a name="getcharacterstream-method-int"></a>Метод getCharacterStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.io.Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCharacterStream задается с помощью метода getCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод считывает только символьные типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Юникоде, такие как nchar, nvarchar, nvarchar(max) и ntext. Для любых других типов данных, включая символьные типы ASCII, будет вызываться исключение. Для считывания типов данных ASCII используйте метод [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream (SQLServerResultSet)](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
