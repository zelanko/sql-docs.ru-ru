---
title: Метод getUnicodeStream (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getUnicodeStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0de79b65-a25e-4028-9cc2-7ac02340115b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad1f452a6fc1f5643a62891f2c2e6caf5334c4a2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910970"
---
# <a name="getunicodestream-method-int"></a>Метод getUnicodeStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде потока символов в Юникоде.  
  
> [!NOTE]  
>  Этот метод является устаревшим в спецификации JDBC, и в случае его вызова создается исключение «не реализовано». Вместо этого следует использовать метод [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getUnicodeStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getUnicodeString определен с помощью метода getUnicodeString в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getUnicodeStream (SQLServerResultSet)](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
