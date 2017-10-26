---
title: "С помощью инструкций с хранимыми процедурами | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f617fdf969c0bdd238b07cb0def1b0a948a4d328
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-statements-with-stored-procedures"></a>Использование инструкций с хранимыми процедурами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Хранимая процедура является процедурой базы данных, схожей с процедурой на других языках программирования, которая хранится в самой базе данных. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], хранимые процедуры могут быть созданы с помощью [!INCLUDE[tsql](../../includes/tsql_md.md)], или с помощью общеязыковой среды выполнения (CLR) и одну из Visual Studio языки программирования типа C# или Visual Basic. Как правило [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимых процедур можно выполнять следующие задачи:  
  
-   принимать входные параметры и возвращать вызывающей процедуре или пакету ряд значений в виде выходных параметров;  
  
-   содержать программные инструкции, которые выполняют операции в базе данных, в том числе вызывающие другие процедуры;  
  
-   возвращать значение состояния вызывающей процедуре или пакету, таким образом передавая сведения об успешном или неуспешном завершении (и причины последнего).  
  
> [!NOTE]  
>  Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимые процедуры в разделе «Основные сведения о хранимых процедурах» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
 Для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью хранимой процедуры, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предоставляет [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), и [ SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы. Выбор класса для использования зависит от того, какие IN (входные) или OUT (выходные) параметры требуются хранимой процедуре. Если хранимая процедура требует без в или ВЫХОДНЫЕ параметры, можно использовать класс SQLServerStatement. Если хранимая процедура будет вызываться несколько раз или требует только параметры IN, можно использовать класс SQLServerPreparedStatement. Если хранимая процедура требует IN и OUT, следует использовать класс SQLServerCallableStatement. Это только когда хранимая процедура требует использования параметров OUT, которые понадобятся дополнительную нагрузку, связанную с использованием класса SQLServerCallableStatement.  
  
> [!NOTE]  
>  Хранимые процедуры могут также возвращать счетчики обновлений и несколько результирующих наборов. Дополнительные сведения см. в разделе [с помощью хранимой процедуры со счетчиком обновлений](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) и [с помощью нескольких результирующих наборов](../../connect/jdbc/using-multiple-result-sets.md).  
  
 При использовании драйвера JDBC для вызова хранимой процедуры с параметрами, необходимо использовать `call` escape-последовательность SQL вместе с [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Полный синтаксис `call` escape-последовательность — следующим образом:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Дополнительные сведения о `call` и других SQL escape-последовательности см. в разделе [с помощью Escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 В этом разделе описываются способы, который можно вызвать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимые процедуры с помощью драйвера JDBC и `call` escape-последовательность SQL.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[С помощью хранимой процедуры без параметров](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|Описывает способы использования драйвера JDBC для запуска хранимых процедур, не содержащих входных или выходных параметров.|  
|[С помощью хранимой процедуры с входными параметрами](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|Описывает способы использования драйвера JDBC для запуска хранимых процедур, содержащих входные параметры.|  
|[С помощью хранимой процедуры с выходными параметрами](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|Описывает способы использования драйвера JDBC для запуска хранимых процедур, содержащих выходные параметры.|  
|[Использование хранимых процедур с состояниями возврата](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|Описывает способы использования драйвера JDBC для запуска хранимых процедур, содержащих возвращаемые значения состояния.|  
|[Использование хранимых процедур со счетчиком обновлений](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|Описывает способы использования драйвера JDBC для запуска хранимых процедур, содержащих счетчики обновления.|  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

