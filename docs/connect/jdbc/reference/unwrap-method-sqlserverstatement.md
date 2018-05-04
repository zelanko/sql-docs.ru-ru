---
title: Метод unwrap (SQLServerStatement) | Документы Microsoft
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
ms.assetid: ce680176-ef04-4e44-bb6c-ec50bd06e7e6
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ddb8472bff74c7c6970d31bb6638aec101cf22b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="unwrap-method-sqlserverstatement"></a>Метод unwrap (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *iface*  
  
 Класс типа **T** определение интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, реализующий указанный интерфейс.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 [Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) метод определен интерфейсом java.sql.Wrapper, который появился в спецификации JDBC 4.0.  
  
 Приложению может потребоваться доступа к расширениям API-интерфейса JDBC, относящиеся к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Метод unwrap поддерживает развертывание в открытые классы, предоставляемые этим объектом, если эти классы реализуют расширения поставщиков.  
  
 При вызове этого метода объект развертывается [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) класса.  
  
 Пример кода см. в разделе [обновление большой образец данных](../../../connect/jdbc/updating-large-data-sample.md), или [метод unwrap &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md).  
  
 Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также  
 [Метод isWrapperFor &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
