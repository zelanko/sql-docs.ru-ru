---
title: Метод setClientInfo (java.lang.String, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 177b92c12ba9daa410de1e65cc3a38b8744f4149
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927163"
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>Метод setClientInfo (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение указанного свойства сведений о клиенте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
  
 Строка, содержащая имя свойства сведений о клиенте, которое необходимо задать.  
  
 *value*  
  
 Строка, содержащая значение, которое необходимо задать свойству сведений о клиенте.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setClientInfo задается с помощью метода setClientInfo в интерфейсе java.sql.Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не поддерживает свойства сведений о клиенте. В драйвере JDBC 2.0 этот метод формирует предупреждение для свойства. Приложения должны использовать метод [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) класса [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) для извлечения предупреждения.  
  
## <a name="see-also"></a>См. также:  
 [Метод setClientInfo (SQLServerConnection)](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
