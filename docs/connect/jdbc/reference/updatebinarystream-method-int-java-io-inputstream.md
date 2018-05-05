---
title: Метод updateBinaryStream (int, java.io.InputStream) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a5b655e723a8af7491c41b9620e21ff78bd364f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Метод updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
