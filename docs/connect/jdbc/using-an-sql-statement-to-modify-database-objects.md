---
title: С помощью инструкции SQL для изменения объектов базы данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b126fb0b5a72688c1801cf8854d8035763c8245f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851499"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Использование инструкции SQL для изменения объектов баз данных 
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы изменить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] объектов базы данных с помощью инструкции SQL, можно использовать [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Метод executeUpdate передаст инструкцию SQL в базу данных для обработки и возвращается значение 0, так как строки не были затронуты.  
  
 Чтобы сделать это, необходимо сначала создать объект SQLServerStatement с помощью [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
> [!NOTE]  
>  Инструкции SQL, изменяющие объекты в базе данных, называются инструкциями языка описания данных DDL. Они включают такие инструкции, как CREATE TABLE, DROP TABLE, CREATE INDEX и DROP INDEX. Дополнительные сведения о типах инструкций DDL, которые поддерживаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, создается инструкция SQL, создаст простую таблицу TestTable в базе данных, инструкция выполняется и выводится возвращаемое значение.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
