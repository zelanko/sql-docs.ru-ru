---
title: Метод updateCharacterStream (java.lang.String, java.io.Reader) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4a44d8a6ea91697c45588c93dfdaf109ac548d75
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784081"
---
# <a name="updatecharacterstream-method-javalangstring-javaioreader"></a>Метод updateCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением потока символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *reader*  
  
 Объект средства чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateCharacterStream указывается с помощью метода updateCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода от объекта средства чтения выбранным текстовым и двоичным столбцам. Сюда входят все текстовые и **двоичные** столбцы, а также столбцы **varbinary**, **varbinary(max)** , **image** и **xml**, но не входят столбцы **определяемых пользователем типов данных**.  
  
 Использование этого метода **изображение**, **текст**, и **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных может повлиять на производительность.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
