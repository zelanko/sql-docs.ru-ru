---
title: Метод isWrapperFor (SQLServerXADataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d612461d-4c3f-46db-b968-ff4c80b2aa7c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 920e47391cbaaeb1e78c8a7a4f440880edab60fd
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803226"
---
# <a name="iswrapperfor-method-sqlserverxadatasource"></a>Метод isWrapperFor (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли этот объект оболочкой указанного интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *iface*  
  
 Объект **класс** определения интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если этот объект реализует интерфейс или упаковывает объект, реализующий интерфейс. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md) и метод [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) определяются с помощью интерфейса java.sql.Wrapper, представленного в спецификации JDBC 4.0.  
  
 Если этот метод возвращает значение true, вызов метода [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) с таким же аргументом будет выполнен успешно.  
  
 Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод unwrap &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)   
 [Методы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Класс SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
