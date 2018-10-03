---
title: Обработка ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 066aa64a529d2066c0dcce50cd2f2aff12dcf948
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758992"
---
# <a name="handling-errors"></a>Обработка ошибок
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] все ошибки базы данных возвращаются в приложение Java в виде исключений через класс [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Приведенные далее методы класса SQLServerException унаследованы от классов java.sql.SQLException и java.lang.Throwable. Их можно использовать для возвращения специфической информации о возникшей ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   getSQLState возвращает стандартный код состояния исключения X/Open или SQL99.  
  
-   getErrorCode возвращает специфический номер ошибки базы данных.  
  
-   getMessage возвращает полный текст исключения. В тексте сообщения об ошибке описывается проблема и зачастую содержатся заполнители для информации, такие как имена объектов, которые вставляются в сообщение об ошибке во время отображения.  
  
-   getNextException возвращает следующий объект SQLServerException или значение null, если нет других объектов исключений для возвращения.  
  
 В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию и создается инструкция SQL неправильного формата, которая не имеет предложения FROM. Далее инструкция выполняется и происходит обработка исключения SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
