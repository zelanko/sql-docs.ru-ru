---
title: "Класс SQLServerParameterMetaData | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 836d6d90405e42df25a9bffb025a6113268560c8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverparametermetadata-class"></a>Класс SQLServerParameterMetaData Class
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет метаданные для параметров подготовленных инструкций.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.lang.Object  
  
 **Реализует:** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>Замечания  
 Для получения метаданных параметров подготовленные инструкции выполняются с параметром SET FMT ONLY. Вызываемые инструкции вызывают процедуру sp_sproc_columns, чтобы получить имена и метаданные для параметров процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

