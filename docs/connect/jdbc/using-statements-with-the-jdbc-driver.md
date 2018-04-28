---
title: Использование инструкций с драйвером JDBC | Документы Microsoft
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
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a70518f53772a37ca9ad2354876a1ec57bea255
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-statements-with-the-jdbc-driver"></a>Использование инструкций с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Можно использовать для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базе данных различными способами. Драйвер JDBC можно использовать для выполнений инструкций SQL для базы данных или вызова хранимых процедур в базе данных, используя как входные, так и выходные параметры. Драйвер JDBC также поддерживает использование escape-последовательностей SQL, счетчиков обновления, автоматически формируемых ключей, а также выполнение обновлений в рамках пакетной операции.  
  
 Драйвер JDBC предоставляет три класса для получения данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных:  
  
1.  [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) — служат для выполнения инструкций SQL без параметров.  
  
2.  [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) — (унаследованные от SQLServerStatement), используемый для выполнения компилированных инструкций SQL, которые могут содержать параметры.  
  
3.  [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) — (унаследованные от SQLServerPreparedStatement) используется для запуска хранимых процедур, которые могут содержать параметры IN, OUT параметров или оба.  
  
 Подразделы данного раздела рассматриваются, как использовать каждый из трех классов инструкций для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)|Описывает, как использовать инструкции SQL с драйвером JDBC для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.|  
|[Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)|Описывает использование хранимых процедур с драйвером JDBC для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.|  
|[Использование нескольких результирующих наборов](../../connect/jdbc/using-multiple-result-sets.md)|Описывает использование драйвера JDBC для извлечения данных из нескольких результирующих наборов.|  
|[Использование escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md)|Описывает использование escape-последовательностей SQL, таких как литералы даты и времени и функции.|  
|[Использование автоматически сформированных ключей](../../connect/jdbc/using-auto-generated-keys.md)|Описывает использование автоматически формируемых ключей.|  
|[Выполнение пакетных операций](../../connect/jdbc/performing-batch-operations.md)|Описывает использование драйвера JDBC для выполнения пакетных операций.|  
|[Обработка сложных инструкций](../../connect/jdbc/handling-complex-statements.md)|Описывает использование драйвера JDBC для выполнения сложных инструкций, выполняющих несколько заданий и могущих вернуть различные типы данных.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
