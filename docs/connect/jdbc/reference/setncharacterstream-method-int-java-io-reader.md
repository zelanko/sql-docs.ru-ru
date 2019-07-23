---
title: Метод setNCharacterStream к объекту Reader-int | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7732746b-eda5-469e-8567-e8546c4d81cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 01e501bbe9ae68b35c4e9b8373b0dfe1f55d9f6f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973910"
---
# <a name="setncharacterstream-method-int-javaioreader"></a>Метод setNCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает указанному параметру заданный объект Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNCharacterStream(int parameterIndex,  
                                                 java.io.Reader value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *value*  
  
 Объект Reader, содержащий значение параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setNCharacterStream задается методом setNCharacterStream в интерфейсе Java. SQL. PreparedStatement.  
  
 Этот метод следует использовать для типов данных **nchar**, **nvarchar**, **ntext**и **XML** .  
  
## <a name="see-also"></a>См. также:  
 [Метод setNCharacterStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
