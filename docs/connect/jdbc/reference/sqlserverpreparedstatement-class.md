---
title: Класс SQLServerPreparedStatement | Документы Microsoft
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
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2494ebfffa6066988bdd979a55cf40d8cd68347e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverpreparedstatement-class"></a>Класс SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет базовую реализацию функциональности подготовленной инструкции JDBC.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** SQLServerStatement  
  
 **Реализует:** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Замечания  
 SQLServerPreparedStatement предоставляет методы, которые позволяют передавать параметры с любым собственным типом Java и множеством типов объектов Java. SQLServerPreparedStatement подготавливает инструкцию, используя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **sp_prepare** хранимой процедуры, а затем использует возвращенный дескриптор инструкции для каждого последующего запуска инструкции, обычно с помощью различных параметры, указываемые пользователем.  
  
 SQLServerPreparedStatement поддерживает пакетную обработку, когда набор подготовленных инструкций выполняется в базе данных единого кругового пути для повышения производительности во время выполнения.  
  
 Этот класс поддерживает развертывание в класс SQLServerPreparedStatement, интерфейс ISQLServerPreparedStatement, интерфейс java.sql.PreparedStatement и классы и интерфейсы, поддерживаемые для развертывания классом SQLServerStatement. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
