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
ms.openlocfilehash: 5300c381b7b64e90cdd9d6a9d3555ffce6a9af52
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67996665"
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
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *reader*  
  
 Объект Reader.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateCharacterStream задается с помощью метода updateCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода от объекта средства чтения выбранным текстовым и двоичным столбцам. Сюда входят все текстовые и **двоичные** столбцы, а также столбцы **varbinary**, **varbinary(max)** , **image** и **xml**, но не входят столбцы **определяемых пользователем типов данных**.  
  
 Использование этого метода при работе с типами данных **image**, **text** и **ntext**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может повлиять на производительность.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
