---
title: "Метод updateBinaryStream (int, java.io.InputStream) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1ede0acb87e477f965696521117c99d410bd0b19
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 Объект, InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateBinaryStream указывается с помощью метода updateBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Использование этого метода для **изображения**, **текст**, и **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типов данных может повлиять на производительность.  
  
 Этот метод передает байты от объекта InputStream для выбранных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] двоичных столбцов, таких как binary, varbinary, varbinary(max), изображение, xml и определяемого пользователем типа. В этом методе не поддерживается обновление символьных столбцов. Чтобы обновить символьный столбец с InputStream, используйте [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) метод.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBinaryStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

