---
title: Использование инструкций в SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d044c1747b13f94c6f7feb902144d51b50af870
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662226"
---
# <a name="using-statements-with-sql"></a>Использование инструкций в SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Когда вы работаете с данным в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] и встроенных инструкций SQL, вы можете использовать разные классы. Выбор используемого класса зависит от типа SQL-инструкции, которую необходимо выполнить.  
  
Если инструкция SQL не содержит параметров IN, используется класс [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), в противном случае используется класс [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Если необходимо использовать инструкцию SQL, которая содержит параметр IN и параметр OUT, необходимо реализовать ее в виде хранимой процедуры и вызвать ее с использованием класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Дополнительные сведения об использовании хранимых процедур см. в разделе [с помощью инструкций, с помощью хранимых процедур](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
В следующих разделах описаны различные сценарии для работы с данными в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью инструкций SQL.  

## <a name="in-this-section"></a>в этом разделе  

| Раздел                                                                                                                        | Описание                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Использование инструкции SQL без параметров](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Описывает порядок использования инструкций SQL, которые не содержат параметров.   |
| [Использование инструкции SQL с параметрами](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Описывает порядок использования инструкций SQL, которые содержат параметры.      |
| [Использование инструкции SQL для изменения объектов баз данных ](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Описывает порядок использования инструкций SQL для изменения объектов базы данных.   |
| [Использование инструкции SQL для изменения данных](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Описывает порядок использования инструкций SQL для изменения данных в базе данных. |
  
## <a name="see-also"></a>См. также:

[Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
