---
title: Обработка ошибок | Документы Microsoft
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
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33f9c9daa495c26b1a1e35869016f0e7382d9d1a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="handling-errors"></a>Обработка ошибок
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], все базы данных ошибки возвращаются в приложение Java в виде исключений через [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) класса. Следующие методы класса SQLServerException унаследованы от классов java.sql.SQLException и java.lang.Throwable. их можно использовать для возвращения специфической информации о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] возникшей ошибки:  
  
-   getSQLState Возвращает стандартный X / Open или SQL99 код состояния исключения.  
  
-   getErrorCode возвращает номер ошибки для конкретной базы данных.  
  
-   getMessage возвращает полный текст исключения. В тексте сообщения об ошибке описывается проблема и зачастую содержатся заполнители для информации, такие как имена объектов, которые вставляются в сообщение об ошибке во время отображения.  
  
-   getNextException возвращает следующий объект SQLServerException или значение null, если нет других объектов исключений для возвращения.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию и создается инструкция SQL неправильного формата, не имеет предложения FROM. Далее инструкция выполняется и происходит обработка исключения SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
