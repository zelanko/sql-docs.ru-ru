---
title: Метод supportsSchemasInTableDefinitions | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSchemasInTableDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3326b1b0-53e2-42ae-9ff7-98e8c7017ffa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 630afabc453ef5ff12a0939d8f5b17d151a994a4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797359"
---
# <a name="supportsschemasintabledefinitions-method-sqlserverdatabasemetadata"></a>Метод supportsSchemasInTableDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, может ли имя схемы использоваться в инструкции определения таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsSchemasInTableDefinitions()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsSchemasInTableDefinitions указывается с помощью метода supportsSchemasInTableDefinitions в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
