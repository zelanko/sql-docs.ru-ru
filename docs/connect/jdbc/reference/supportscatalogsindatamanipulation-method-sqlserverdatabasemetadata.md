---
title: Метод supportsCatalogsInDataManipulation | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInDataManipulation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee1af47a-4c04-4391-83a5-54ced80218c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c35d0f312dde450f33c9c295e092d9bc594b87f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826922"
---
# <a name="supportscatalogsindatamanipulation-method-sqlserverdatabasemetadata"></a>Метод supportsCatalogsInDataManipulation (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, может ли имя каталога использоваться в инструкции обработки данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsCatalogsInDataManipulation()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsCatalogInDataManipulation указывается с помощью метода supportsCatalogInDataManipulation в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
