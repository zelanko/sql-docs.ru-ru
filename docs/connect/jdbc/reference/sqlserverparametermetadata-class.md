---
title: Класс SQLServerParameterMetaData | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54e6c4fd85ed8f658019d6a01a394317f764c9af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
