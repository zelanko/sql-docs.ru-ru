---
title: "Метод updateCharacterStream (int, java.io.Reader) | Документы Microsoft"
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
ms.assetid: 4dddf885-0482-4776-8e9a-69f6c6270931
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74898560434c44891a92e38940b521785cb3a5e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updatecharacterstream-method-int-javaioreader"></a>Метод updateCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением потока символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateCharacterStream(int columnIndex,  
                                  java.io.Reader x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 Объект модуля чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateCharacterStream указывается с помощью метода на updateCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода от объекта модуля чтения выделенный текст и двоичные столбцы. Сюда входят все текстовые столбцы и **двоичных**, **varbinary**, **varbinary(max)**, **изображения**, и **xml**столбцы, но не **определяемого пользователем типа** столбцов.  
  
 Использование этого метода для **изображения**, **текст**, и **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типов данных может повлиять на производительность.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

