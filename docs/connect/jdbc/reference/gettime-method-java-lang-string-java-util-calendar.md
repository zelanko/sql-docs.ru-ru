---
title: "Метод getTime (java.lang.String, java.util.Calendar) | Документы Microsoft"
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
- SQLServerCallableStatement.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d4c67c2-a3c8-4a26-a159-89c5d63fda0b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eaa53198cb3a96725f3304a7bb8fa88c67df73b1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="gettime-method-javalangstring-javautilcalendar"></a>Метод getTime (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта java.sql.Time на языке программирования, заданному имени параметра, используя данный объект календаря Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *Клиентская лицензия*  
  
 Объект календаря.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект времени.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTime указывается с помощью getTime метода в интерфейсе java.sql.CallableStatement.  
  
 См. в диаграмму с названием «Преобразования метода считывания» [основные сведения о преобразованиях типов данных](../../../connect/jdbc/understanding-data-type-conversions.md) также просмотреть, какие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типов данных можно получить с помощью этого метода.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTime &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

