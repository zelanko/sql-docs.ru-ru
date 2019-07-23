---
title: Метод isWrapperFor (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c35cad678ce4f9b6008b656302d4767bad9b1244
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977061"
---
# <a name="iswrapperfor-method-sqlserverstatement"></a>Метод isWrapperFor (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *IFACE*  
  
 **Класс** , определяющий интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если этот объект реализует интерфейс или упаковывает объект, реализующий интерфейс. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) и метод [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) определяются интерфейсом java.sql.Wrapper, представленного в JDBC 4.0.  
  
 Если этот метод возвращает значение true, вызов метода [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) с таким же аргументом будет выполнен успешно.  
  
 Пример кода см. в разделе [Пример обновления больших данных](../../../connect/jdbc/updating-large-data-sample.md).  
  
 Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Распаковка метода &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
