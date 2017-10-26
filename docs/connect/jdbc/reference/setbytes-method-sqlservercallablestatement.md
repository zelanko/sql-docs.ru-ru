---
title: "Метод setBytes (SQLServerCallableStatement) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.setBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f264f1a6-ee35-4eaf-81d8-ecf99f03b35d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bb71147830da79a89954a968bfbe6fcac304a581
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setbytes-method-sqlservercallablestatement"></a>Метод setBytes (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру заданный массив **байтов** значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setBytes(java.lang.String sCol,  
                     byte[] b)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *b*  
  
 Массив **байтов** значения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 В предыдущей версии драйвера, можно использовать SQLServerCallableStatement.setBytes для преобразования значений между массивами байтов и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип данных **даты**, **время**, **datetime2 **, или **datetimeoffset**. Теперь при вызове этого метода с такими типами данных возникает исключение, указывающее, что такое преобразование не поддерживается.  
  
 Этот метод setBytes указывается с помощью метода setBytes в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

