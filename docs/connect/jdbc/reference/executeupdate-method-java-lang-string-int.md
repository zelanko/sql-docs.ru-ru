---
title: Метод executeUpdate (java.lang.String, int) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c52a20e-527e-4d14-9a5a-4cd195aac8ed
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c173fa5ed1c2d431038cb6ffd8b917d1d521e27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="executeupdate-method-javalangstring-int"></a>Метод executeUpdate (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и сигналы [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с помощью определенного флага о ли автоматически созданные ключи, созданные этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта должны быть доступны для загрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               int flag)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
 *flag*  
  
 **Int** значение, указывающее, если автоматически сформированные ключи должны быть доступными. Это должна быть одна из следующих констант:  
  
 RETURN_GENERATED_KEYS  
  
 NO_GENERATED_KEYS  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** указывает число обработанных строк, либо значение 0 для инструкций DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод executeUpdate указывается с помощью метода executeUpdate в интерфейсе java.sql.Statement.  
  
 Если выполнение хранимой процедуры приведет к счетчика обновлений, больше единицы либо сформировано более одного результирующего набора, используйте [выполнение](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод для выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Метод executeUpdate &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
