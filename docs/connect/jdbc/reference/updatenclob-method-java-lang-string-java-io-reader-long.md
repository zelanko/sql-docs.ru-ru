---
title: Метод updateNClob (java.lang.String, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ad5c8d9b-f8c8-4ddf-85c8-23420bba54ee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 76271038cab9fbf46194b2f6d1302f30ecbd26ac
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798378"
---
# <a name="updatenclob-method-javalangstring-javaioreader-long"></a>Метод updateNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с помощью заданного объекта **Reader**, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение **String**, которое указывает метку столбца.  
  
 *reader*  
  
 Объект средства чтения.  
  
 *length*  
  
 Количество символов в данных параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getNClob определен с помощью метода getNClob в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только в **nvarchar(max)** , **ntext**, и **xml** столбцов. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
