---
title: Метод unwrap (SQLServerXADataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d97c99b3-2224-4abb-8b32-40aff49fe759
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b1ef2e7b05361ece8e54847b3c4d0d1df5ace08
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926079"
---
# <a name="unwrap-method-sqlserverxadatasource"></a>Метод unwrap (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает объект, реализующий указанный интерфейс для доступа к методам, относящимся к драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Параметры  
 *iface*  
  
 Класс типа **T**, определяющий интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, реализующий указанный интерфейс.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) определен интерфейсом java.sql.Wrapper, который появился в спецификации JDBC 4.0.  
  
 Приложению может потребоваться доступ к расширениям интерфейса API JDBC, предоставляемым драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Метод unwrap поддерживает развертывание в открытые классы, предоставляемые этим объектом, если эти классы реализуют расширения поставщиков.  
  
 Класс [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md) расширяет класс [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), который, в свою очередь, является расширенным классом [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md). При вызове этого метода объект развертывается в следующие классы: [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) и [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
 Дополнительные сведения см. в статье об [интерфейсах и программах-оболочках](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Класс SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
