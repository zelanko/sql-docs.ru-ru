---
title: Класс SQLServerPreparedStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 96d2e01d4ca8d38b79906ee31cc5b50df0d8cb25
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970769"
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
  
## <a name="remarks"></a>Remarks  
 SQLServerPreparedStatement предоставляет методы, позволяющие указать для параметров любые типы машинного кода Java и различные типы объектов Java. Класс SQLServerPreparedStatement выполняет подготовку инструкции с помощью хранимой процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sp_prepare**, а затем использует возвращенный дескриптор инструкции для каждого последующего выполнения инструкции (обычно при этом используются различные параметры, указываемые пользователем).  
  
 SQLServerPreparedStatement поддерживает пакетную организацию, когда набор подготовленных инструкций выполняется за одно обращение к базе данных, чтобы повысить производительность выполнения.  
  
 Этот класс поддерживает распаковку в класс SQLServerPreparedStatement, интерфейс ISQLServerPreparedStatement, Java. SQL. PreparedStatement, а также классы и интерфейсы, поддерживаемые SQLServerStatement для распаковки. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
