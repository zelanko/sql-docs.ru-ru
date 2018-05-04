---
title: Класс SQLServerException | Документы Microsoft
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
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56766dec21b0e823174eeccbaf16a02de2b5578a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverexception-class"></a>Класс SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет неуспешное или неполное выполнение инструкции SQL.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.sql.SQLException  
  
 **Реализует:** java.io.Serializable  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Замечания  
 Класс SQLServerException обрабатывает коды состояний SQL 92 и XOPEN. Их можно переключать с помощью свойства соединения, задаваемого пользователем. Исключения записываются в любые указанные открытые файлы журнала.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
