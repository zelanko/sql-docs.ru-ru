---
title: Метод isWrapperFor (SQLServerCallableStatement) | Документы Microsoft
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
ms.topic: article
ms.assetid: 71156863-3588-453e-b5a5-0573b2c1bebf
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2bf03b3e0ea5a2879dd7536a5f9c730953fb8acf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="iswrapperfor-method-sqlservercallablestatement"></a>Метод isWrapperFor (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.  
  
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
 [IsWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md) метод и [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) метод определяются интерфейсом java.sql.Wrapper, который появился в JDBC 4.0.  
  
 Если этот метод возвращает **true**, вызов [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) с тем же аргументом будет выполнена успешно.  
  
 Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также  
 [Метод unwrap &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
