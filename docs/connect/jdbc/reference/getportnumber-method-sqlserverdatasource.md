---
title: Метод getPortNumber (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20850d10352a583abd7e0a8bd9747b6346ec3aaa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980834"
---
# <a name="getportnumber-method-sqlserverdatasource"></a>Метод getPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий номер порта, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, содержащее текущий номер порта.  
  
## <a name="remarks"></a>Remarks  
 Номер порта — это номер порта TCP/IP, который используется при открытии соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через сокет. Если свойство portNumber не задано, то метод getPortNumber возвращает значение по умолчанию (1433).  
  
> [!NOTE]  
>  Метод [setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) не выполняет проверку диапазона для переданного значения порта. Вы можете передать недопустимые номера гражданским правонарушением, например 99999, без активации ошибки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
