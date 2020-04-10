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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2ed370fdb002563203ffbc403bda54acef688af
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925331"
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
  
  
