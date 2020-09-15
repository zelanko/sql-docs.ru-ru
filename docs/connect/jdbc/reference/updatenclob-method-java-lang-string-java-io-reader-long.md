---
description: Метод updateNClob (java.lang.String, java.io.Reader, long)
title: Метод updateNClob (java.lang.String, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ad5c8d9b-f8c8-4ddf-85c8-23420bba54ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6bd151c08cff98bba419d425d24ac0160ffc42d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431266"
---
# <a name="updatenclob-method-javalangstring-javaioreader-long"></a>Метод updateNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с помощью заданного объекта **Reader**, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение **String**, которое указывает метку столбца.  
  
 *reader*  
  
 Объект Reader.  
  
 *length*  
  
 Количество символов в данных параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNClob определен с помощью метода updateNClob в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только для столбцов **nvarchar(max)**, **ntext** и **xml**. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
