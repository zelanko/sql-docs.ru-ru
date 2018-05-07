---
title: Использование метаданных о параметрах | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2ff7d2646c0a3838b8a0dc72249b73e64227dd7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-parameter-metadata"></a>Использование метаданных о параметрах
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Запрос [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) объект сведения о параметрах, которые они содержат [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует [ SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) класса. Этот класс содержит многочисленные поля и методы, которые возвращают сведения в виде одного значения.  
  
 Чтобы создать объект SQLServerParameterMetaData, можно использовать [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) методам для классов SQLServerPreparedStatement и SQLServerCallableStatement.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getParameterMetaData класса SQLServerCallableStatement используется для возврата объекта SQLServerParameterMetaData, а затем различных методы SQLServerParameterMetaData объекта используются для отображения сведений о типе и режиме параметров, содержащихся в хранимой процедуре HumanResources.uspUpdateEmployeeHireInfo.  
  
 [!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  
    
> [!NOTE]  
Существуют некоторые ограничения при использовании класса SQLServerParameterMetaData с подготовленными инструкциями. 
**Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server**: при использовании SQL Server 2008 или 2008 R2, драйвер JDBC поддерживает инструкции SELECT, DELETE, INSERT и UPDATE, при условии, что эти инструкции не содержит вложенные запросы или соединения.  

Запросы MERGE также не поддерживаются для класса SQLServerParameterMetaData при использовании SQL Server 2008 или 2008 R2. Для SQL Server 2012 и более поздних версий поддерживаются метаданные параметров со сложными запросами.  

Получение метаданных параметра для зашифрованных столбцов не поддерживаются. **С Microsoft JDBC Driver 4.1 и 4.2 для SQL Server**: драйвер JDBC поддерживает инструкции SELECT, DELETE, INSERT и UPDATE, при условии, что эти инструкции не содержит вложенные запросы или соединения. Запросы MERGE также не поддерживается для класса SQLServerParameterMetaData.  
  
  
