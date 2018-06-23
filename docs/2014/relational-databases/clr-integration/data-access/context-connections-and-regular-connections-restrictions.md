---
title: Ограничения обычных и контекстных соединений | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0d266b75dad229a0784606af112c249728a112c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190984"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Ограничения обычных и контекстных соединений
  В этом разделе содержатся сведения об ограничениях, связанных с кодом, выполняемым в [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] через контекстные и обычные соединения.  
  
## <a name="restrictions-on-context-connections"></a>Ограничения контекстных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к контекстным соединениям.  
  
-   В определенное время для заданного соединения может существовать только одно открытое контекстное соединение. Если имеется несколько инструкций, параллельно выполняемых в отдельных соединениях, каждая из них может иметь собственное контекстное соединение. Ограничение не влияет на параллельные запросы из различных соединений, оно влияет только на конкретный запрос в отдельном соединении.  
  
-   Режим MARS не поддерживается в контекстных соединениях.  
  
-   Класс `SqlBulkCopy` не работает в контекстных соединениях.  
  
-   Пакетное обновление не поддерживается в контекстных соединениях.  
  
-   `SqlNotificationRequest` нельзя использовать с командами, применяемыми в контекстном соединении.  
  
-   Отмена команд, применяемых в контекстном соединении, не поддерживается. Метод `SqlCommand.Cancel` не учитывает запрос, не сообщая об этом.  
  
-   Никакие другие ключевые слова строки соединения не могут использоваться при использовании «context connection=true».  
  
-   Свойство `SqlConnection.DataSource` возвращает вместо имени экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значение NULL, если строка соединения для `SqlConnection` равна «context connection=true».  
  
-   Установка свойства `SqlCommand.CommandTimeout` не имеет значения, если команда выполняется в контекстном соединении.  
  
## <a name="restrictions-on-regular-connections"></a>Ограничения обычных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к обычным соединениям.  
  
-   Асинхронное применение команд к внутренним серверам не поддерживается. Если в строке соединения содержится «async=true», по при последующем выполнении команды возникает исключение `System.NotSupportedException`. Отображается сообщение: «Асинхронная обработка не поддерживается при выполнении в процессе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   Объект `SqlDependency` не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Контекстное соединение](context-connection.md)  
  
  