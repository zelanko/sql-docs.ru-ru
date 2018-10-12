---
title: Класс SQLServerException | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: cfcc73705d04b3d3efa7515f74676b0eda120323
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680283"
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
 Класс SQLServerException обрабатывает коды состояний SQL 92 и XOPEN. Их можно переключать с помощью свойства соединения, задаваемого пользователем. Исключения записываются в любые указанные открытые файлы журнала.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
