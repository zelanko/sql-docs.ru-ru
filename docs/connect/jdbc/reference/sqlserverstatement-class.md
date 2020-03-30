---
title: Класс SQLServerStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89547655fd734ca9e6e340d94832dea5816f2733
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970375"
---
# <a name="sqlserverstatement-class"></a>Класс SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет базовую реализацию функциональности инструкции JDBC.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализация.** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Remarks  
 Класс SQLServerStatement также предоставляет набор реализаций методов базового класса для подготовленных и вызываемых инструкций JDBC. Основной задачей класса SQLServerStatement является выполнение инструкций SQL с дальнейшей передачей количества обновлений и результирующих наборов в приложение пользователя.  
  
 Этот класс поддерживает распаковку в класс SQLServerStatement, интерфейс SQLServerStatement и интерфейс java.sql.Statement interface. См. сведения об [интерфейсах и программах-оболочках](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
