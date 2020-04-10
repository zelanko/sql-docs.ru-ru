---
title: Метод updateBinaryStream (int, java.io.InputStream) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3c0106d85f00bf406f8b79b1df3c6562fd56e7ae
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925557"
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>Метод updateBinaryStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение двоичного потока в указанном столбце.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBinaryStream задается с помощью метода updateBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Использование этого метода при работе с типами данных **image**, **text** и **ntext**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может повлиять на производительность.  
  
 Этот метод передает байты от объекта InputStream выбранным двоичным столбцам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], таким как binary, varbinary, varbinary(max), image, xml и udt. В этом методе не поддерживается обновление символьных столбцов. Для обновления с помощью InputStream символьных столбцов используйте метод [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
