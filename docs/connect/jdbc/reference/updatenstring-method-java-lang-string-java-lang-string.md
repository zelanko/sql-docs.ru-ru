---
title: Метод updateNString (java.lang.String, java.lang.String) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0fdc853608cf1897e97e08aac673aff78df00aef
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67998552"
---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>Метод updateNString (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение **String** с помощью указанной метки столбцов в заданном столбце.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *nString*  
  
 Объект **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNString задается с помощью метода updateNString в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает **строковое значение** Java в выбранные столбцы **nchar**, **nvarchar(max)** , **ntext** и **xml**. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
