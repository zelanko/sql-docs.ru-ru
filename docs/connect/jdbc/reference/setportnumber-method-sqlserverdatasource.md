---
title: Метод setPortNumber (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 304d63f7822990c4d8e4a9c0787c9e688c222580
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799628"
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Метод setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер порта, используемого для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Параметры  
 *portNumber*  
  
 Значение типа **int**, содержащее номер порта.  
  
## <a name="remarks"></a>Remarks  
 Номер порта — это номер порта TCP/IP, который используется при открытии соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через сокет. Если свойство portNumber не задано, то метод [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) возвращает значение по умолчанию (1433).  
  
> [!NOTE]  
>  Метод setPortNumber не выполняет проверку допустимости диапазона для переданное значение порта. Вы можете передать номер порта, который не является допустимым, например 99999, не вызовет ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
