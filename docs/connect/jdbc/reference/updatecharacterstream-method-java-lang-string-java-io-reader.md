---
title: Метод updateCharacterStream (java.lang.String, java.io.Reader) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9c755a658b0a63966a2db4be4e55b09b1004a0a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850599"
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
  
 Объект **строка** , содержащее метку столбца.  
  
 *Модуль чтения*  
  
 Объект модуля чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateCharacterStream указывается с помощью метода на updateCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода от объекта модуля чтения выделенный текст и двоичные столбцы. Сюда входят все текстовые столбцы и **двоичных**, **varbinary**, **varbinary(max)**, **изображения**, и **xml**столбцы, но не **определяемого пользователем типа** столбцов.  
  
 Использование этого метода для **изображения**, **текст**, и **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типов данных может повлиять на производительность.  
  
## <a name="see-also"></a>См. также  
 [Метод updateCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
