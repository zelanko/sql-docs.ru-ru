---
title: Метод isWrapperFor (SQLServerConnectionPoolDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09ed10eb-6e46-437b-a7c0-3c55574aad38
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9d97bb3ac6f6e888424a133abdca50abfe80c22d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80911916"
---
# <a name="iswrapperfor-method-sqlserverconnectionpooldatasource"></a>Метод isWrapperFor (SQLServerConnectionPoolDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли этот объект оболочкой указанного интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *iface*  
  
 **Класс**, определяющий интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если этот объект реализует интерфейс или упаковывает объект, реализующий интерфейс. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md) и метод [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md) определяются с помощью интерфейса java.sql.Wrapper, представленного в спецификации JDBC 4.0.  
  
 Если этот метод возвращает значение true, вызов метода [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md) с таким же аргументом будет выполнен успешно.  
  
 Дополнительные сведения см. в статье об [интерфейсах и программах-оболочках](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод unwrap (SQLServerConnectionPoolDataSource)](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)   
 [Методы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Элементы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Класс SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
