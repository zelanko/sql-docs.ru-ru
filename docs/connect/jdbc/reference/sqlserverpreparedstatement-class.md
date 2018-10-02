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
manager: craigg
ms.openlocfilehash: 529f93e136ac2515e13fb69866ff5b570557cd0b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741272"
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
  
 Этот класс поддерживает развертывание в класс SQLServerPreparedStatement, интерфейс ISQLServerPreparedStatement, интерфейс java.sql.PreparedStatement и классы и интерфейсы, поддерживаемые для развертывания классом SQLServerStatement. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
