---
description: Метод getTime (java.lang.String, java.util.Calendar)
title: Метод getTime (java.lang.String, java.util.Calendar) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d4c67c2-a3c8-4a26-a159-89c5d63fda0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47ecebd8694c8fc7d89d88b96599eeabd0c55fa0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434206"
---
# <a name="gettime-method-javalangstring-javautilcalendar"></a>Метод getTime (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение заданного параметра в виде объекта java.sql.Time на языке программирования Java по имени параметра, используя указанный объект Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
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
  
  
