---
title: Метод getTime (int, java.util.Calendar) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 87b7fbaf-7149-494f-b3b2-16b468a8ebf1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 286a7437601abf57791a0312dc325590c7e1b981
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927457"
---
# <a name="gettime-method-int-javautilcalendar"></a>Метод getTime (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение заданного параметра в виде объекта java.sql.Time на языке программирования Java по индексу параметра, используя указанный объект Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *cal*  
  
 Объект Calendar.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Time.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTime указывается методом getTime в интерфейсе java.sql.CallableStatement.  
  
 См. диаграмму с названием "Преобразования метода считывания" в статье с [основными сведениями о преобразованиях типов данных](../../../connect/jdbc/understanding-data-type-conversions.md), чтобы узнать, какие типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно извлечь с использованием этого метода.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTime (SQLServerCallableStatement)](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
