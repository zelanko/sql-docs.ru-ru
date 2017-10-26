---
title: "Класс SQLServerConnection | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a3beda0e5629888804b522e5c4e3123e0b959ba8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnection-class"></a>Класс SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет соединение JDBC с [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует:** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md), java.io.Serializable  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Замечания  
 SQLServerConnection поддерживает пулы соединений JDBC и может представлять физическое соединение JDBC или логическое соединение JDBC. SQLServerConnection управляет транзакциями для всех инструкций, созданных из него, и может участвовать в распределенных транзакциях XA, управляемых через адаптер XAResource.  
  
 SQLServerConnection управляет пулом дескрипторов подготовленных инструкций. Подготовленные инструкции готовятся один раз и обычно выполняются несколько раз с различными значениями параметров. Кроме того, подготовленные транзакции сохраняются после закрытия логических соединений (входящих в пул).  
  
> [!NOTE]  
>  SQLServerConnection не является потокобезопасным. Однако несколько инструкций, созданных из одного соединения, можно обрабатывать одновременно в параллельных потоках.  
  
 Этот класс поддерживает развертывание в класс SQLServerConnection, java.sql.connection интерфейс и интерфейс ISQLServerConnection. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

