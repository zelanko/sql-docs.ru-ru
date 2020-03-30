---
title: Метод executeUpdate (java.lang.String, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c52a20e-527e-4d14-9a5a-4cd195aac8ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 783058a764963637f2c91808424bac7bdd403c02
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954758"
---
# <a name="executeupdate-method-javalangstring-int"></a>Метод executeUpdate (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и с помощью определенного флага уведомляет драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] о том, что автоматически сформированные ключи, созданные этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), должны быть доступны для получения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               int flag)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
 *flag*  
  
 Значение типа **int**, которое указывает, нужно ли обеспечить доступ к автоматически формируемым ключам. Это должна быть одна из следующих констант:  
  
 RETURN_GENERATED_KEYS  
  
 NO_GENERATED_KEYS  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее либо число обработанных строк, либо значение 0 для инструкций языка DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод executeUpdate определен с помощью метода executeUpdate в интерфейсе java.sql.Statement.  
  
 Если в результате выполнения хранимой процедуры счетчик обновлений больше единицы либо сформировано больше одного результирующего набора, используйте для выполнения хранимой процедуры метод [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод executeUpdate &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
