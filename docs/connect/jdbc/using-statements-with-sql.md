---
title: Использование инструкций в SQL | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 553c0e742b34406b23a68f1403c372dcc7080088
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69025832"
---
# <a name="using-statements-with-sql"></a>Использование инструкций в SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Когда вы работаете с данным в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] и встроенных инструкций SQL, вы можете использовать разные классы. Выбор используемого класса зависит от типа SQL-инструкции, которую необходимо выполнить.  
  
Если инструкция SQL не содержит параметров IN, используется класс [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), в противном случае используется класс [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Если необходимо использовать инструкцию SQL, которая содержит параметр IN и параметр OUT, необходимо реализовать ее в виде хранимой процедуры и вызвать ее с использованием класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). См. сведения об [использовании инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
В следующих разделах описаны различные сценарии для работы с данными в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкций SQL.  

## <a name="in-this-section"></a>в этом разделе  

| Раздел                                                                                                                        | Description                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Использование инструкции SQL без параметров](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Описывает порядок использования инструкций SQL, которые не содержат параметров.   |
| [Использование инструкции SQL с параметрами](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Описывает порядок использования инструкций SQL, которые содержат параметры.      |
| [Использование инструкции SQL для изменения объектов баз данных](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Описывает порядок использования инструкций SQL для изменения объектов базы данных.   |
| [Использование инструкции SQL для изменения данных](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Описывает порядок использования инструкций SQL для изменения данных в базе данных. |
  
## <a name="see-also"></a>См. также раздел

[Использование инструкций с JDBC Driver](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
