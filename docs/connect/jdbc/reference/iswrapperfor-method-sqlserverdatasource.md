---
title: Метод isWrapperFor (SQLServerDataSource) | Документы Microsoft
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
ms.assetid: f77af027-c021-4a17-b264-1ee592bfdd84
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1862175c31876c2391d2076929d146ec7a5a31a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="iswrapperfor-method-sqlserverdatasource"></a>Метод isWrapperFor (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли этот объект источника данных оболочкой указанного интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *iface*  
  
 Объект **класса** определение интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если этот объект реализует интерфейс или упаковывает объект, реализующий интерфейс. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md) метод и [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md) метод определяются интерфейсом java.sql.Wrapper, который появился в спецификации JDBC 4.0.  
  
 Если этот метод возвращает значение true, вызов метода [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md) с тем же аргументом будет выполнена успешно.  
  
 Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также  
 [Метод unwrap &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)   
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
