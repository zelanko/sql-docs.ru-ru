---
title: Метод getCatalogSeparator (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogSeparator
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0bbd6842-7210-432a-bef4-e15a63f5cc96
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a17b7512345e0630ee891771eb5c4e003db6628e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928195"
---
# <a name="getcatalogseparator-method-sqlserverdatabasemetadata"></a>Метод getCatalogSeparator (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение типа **String**, используемое базой данных в качестве разделителя между каталогом и именем таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getCatalogSeparator()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее разделитель каталога.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCatalogSeparator определен с помощью метода getCatalogSeparator в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] этот метод возвращает символ точки ("."), который используется как разделитель каталога.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
