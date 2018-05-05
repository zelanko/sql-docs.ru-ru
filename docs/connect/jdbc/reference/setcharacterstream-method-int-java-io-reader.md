---
title: Метод setCharacterStream (int, java.io.Reader) | Документы Microsoft
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
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8004a4bda2cb68beb619db852dbef083d84c7d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setcharacterstream-method-int-javaioreader"></a>Метод setCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру java.io.Reader указанный объект.  
  
> [!NOTE]  
>  Эта функция реализована, начиная с [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] драйвер JDBC версии 2.0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** указывает номер параметра.  
  
 *Модуль чтения*  
  
 Java.io.Reader объект, содержащий данные в Юникоде.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setCharacterStream указывается с помощью метода setCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также  
 [Метод setCharacterStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
