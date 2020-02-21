---
title: Класс SQLServerException | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40474f747022c34994dba9f34dbed15f1791c2af
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971156"
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
  
## <a name="remarks"></a>Remarks  
 Класс SQLServerException обрабатывает коды состояний SQL 92 и XOPEN. Их можно переключать с помощью свойства соединения, задаваемого пользователем. Исключения записываются в любые указанные открытые файлы журнала.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
