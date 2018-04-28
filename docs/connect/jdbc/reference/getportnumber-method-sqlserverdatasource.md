---
title: Метод getPortNumber (SQLServerDataSource) | Документы Microsoft
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
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cc115a11669b586a9e8271aad44e4ce11359c91
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getportnumber-method-sqlserverdatasource"></a>Метод getPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий номер порта, используемый для взаимодействия с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, содержащее текущий номер порта.  
  
## <a name="remarks"></a>Замечания  
 Номер порта — номер порта TCP/IP, используемый при открытии подключения к сокету [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если свойство portNumber не задано, то метод getPortNumber возвращает значение по умолчанию (1433).  
  
> [!NOTE]  
>  [SetPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) метод не выполняет проверку диапазона для переданное значение порта. Можно передавать недопустимые номера, которые не являются допустимыми, например 99999, не вызовет ошибку.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
