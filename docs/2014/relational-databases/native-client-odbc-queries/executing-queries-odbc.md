---
title: Выполнение запросов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b924596a4071f59175faa629006e9e5b220f66ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200234"
---
# <a name="executing-queries-odbc"></a>Выполнение запросов (ODBC)
  После того, как приложение ODBC инициализирует дескриптор соединения и подключается к источнику данных, оно выделяет один или несколько дескрипторов инструкций на дескриптор соединения. Приложение может затем выполнить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций с дескриптором инструкции. Общая последовательность событий при выполнении инструкции SQL.  
  
1.  Установите необходимые атрибуты инструкции.  
  
2.  Сформируйте инструкцию.  
  
3.  Выполните инструкцию.  
  
4.  Получите результирующие наборы.  
  
 После того, как приложение получит все строки во всех результирующих наборах, возвращенных инструкцией SQL, оно может выполнить другой запрос на том же дескрипторе инструкции. Если приложение определяет, что он не требуется извлекать все строки в некотором результирующем наборе, его можно отменить остаток результирующего набора с помощью вызова [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) или [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).  
  
 Если в приложении ODBC необходимо несколько раз выполнить одну инструкцию SQL с различными данными, используйте маркер параметра, обозначенный вопросительным знаком (?) при построении инструкции SQL:  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Каждый маркер параметра затем подключаются к программной переменной путем вызова [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md).  
  
 После того, как будут вызваны все инструкции SQL и обработаны их результирующие наборы, приложение освобождает дескриптор инструкции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает несколько дескрипторов инструкций на один дескриптор соединения. Управление транзакциями осуществляется на уровне соединения, поэтому вся работа, выполняемая со всеми дескрипторами инструкций на одном дескрипторе соединения, управляется как часть одной транзакции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выделение дескриптора инструкции](allocating-a-statement-handle.md)  
  
-   [Конструирование инструкций SQL &#40;ODBC&#41;](constructing-an-sql-statement-odbc.md)  
  
-   [Конструирование инструкций SQL для курсоров](constructing-sql-statements-for-cursors.md)  
  
-   [Использование параметров инструкции](using-statement-parameters.md)  
  
-   [Выполнение инструкций &#40;ODBC&#41;](executing-statements/executing-statements-odbc.md)  
  
-   [Освобождение дескриптора инструкции](freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
