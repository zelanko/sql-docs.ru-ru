---
title: Метод setPortNumber (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 0c171e8fb78553275d6a1f5d4bcce485a470f94a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973190"
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
>  Метод setPortNumber не выполняет проверку диапазонов для переданного значения порта. Вы можете передать недопустимый номер порта, например 99999, и это не вызовет ошибки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
