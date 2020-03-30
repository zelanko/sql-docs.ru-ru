---
title: Метод updateNCharacterStream (int, java.io.Reader) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fc746413-bdbf-4109-aee0-385a1270c847
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ce089832227a9f44cd1adfd0a4682b53002a2fc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67998713"
---
# <a name="updatencharacterstream-method-int-javaioreader"></a>Метод updateNCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением потока символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNCharacterStream(int columnIndex,  
                                  java.io.Reader x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект Reader.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNCharacterStream задается с помощью метода updateNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода из объекта Reader выбранным столбцам **nchar**, **nvarchar(max)** , **ntext** и **xml**. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
