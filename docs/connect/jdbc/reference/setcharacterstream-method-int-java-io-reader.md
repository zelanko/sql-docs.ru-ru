---
title: Метод setCharacterStream (int, java.io.Reader) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d97ed3360db0d1a81f71225e4664c6624cb9da37
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974699"
---
# <a name="setcharacterstream-method-int-javaioreader"></a>Метод setCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру заданный объект java.io.Reader.  
  
> [!NOTE]
>  Эта функция используется начиная с драйвера [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC версии 2.0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение **int**, определяющее номер параметра.  
  
 *reader*  
  
 Объект java.io.Reader, содержащий данные в Юникоде.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream задается с помощью метода setCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setCharacterStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
