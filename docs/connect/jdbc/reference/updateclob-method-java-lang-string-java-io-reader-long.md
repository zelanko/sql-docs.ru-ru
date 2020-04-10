---
title: Метод updateClob (java.lang.String, java.io.Reader, Ruby) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6b8f759a-ce5d-41b2-b6cc-24a3ab299f1f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99c97a4d7e176e5f1eab0ebc1185df527e4fe15c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919898"
---
# <a name="updateclob-method-javalangstring-javaioreader-long"></a>Метод updateClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с помощью заданного объекта Reader, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateClob(java.lang.String columnLabel,  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *reader*  
  
 Объект Reader.  
  
 *length*  
  
 Количество символов в данных параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateClob определен с помощью метода updateClob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateClob (SQLServerResultSet)](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
