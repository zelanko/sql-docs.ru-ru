---
title: Метод getSuperTables (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSuperTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 085461de-367b-4832-88aa-010813d2bc41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1caaa96d303e892d9bd729181d7dba1f327b6852
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926137"
---
# <a name="getsupertables-method-sqlserverdatabasemetadata"></a>Метод getSuperTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает описания иерархий таблиц, определенных в конкретной схеме этой базы данных.  
  
> [!NOTE]  
>  В настоящее время этот метод не поддерживается в [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При использовании этот метод всегда возвращает пустой результирующий набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getSuperTables(java.lang.String catalog,  
                                         java.lang.String schemaPattern,  
                                         java.lang.String tableNamePattern)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *schemaPattern*  
  
 Значение типа **String**, содержащее шаблон имени схемы.  
  
 *TableNamePattern*  
  
 Значение типа **String**, содержащее шаблон имени таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSuperTables определен с помощью метода getSuperTables в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
