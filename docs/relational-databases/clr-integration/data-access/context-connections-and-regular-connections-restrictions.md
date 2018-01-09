---
title: "Ограничения обычных и контекстных соединений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b7986fadc999eaa721e774ff95b04aa5b861c41
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Контекстные соединения и обычные соединения - ограничения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В этом разделе содержатся сведения об ограничениях, связанных с кодом, выполняемым в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через контекстные и обычные соединения.  
  
## <a name="restrictions-on-context-connections"></a>Ограничения контекстных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к контекстным соединениям.  
  
-   В определенное время для заданного соединения может существовать только одно открытое контекстное соединение. Если имеется несколько инструкций, параллельно выполняемых в отдельных соединениях, каждая из них может иметь собственное контекстное соединение. Ограничение не влияет на параллельные запросы из различных соединений, оно влияет только на конкретный запрос в отдельном соединении.  
  
-   Режим MARS не поддерживается в контекстных соединениях.  
  
-   Класс **SqlBulkCopy** не работает в контекстных соединениях.  
  
-   Пакетное обновление не поддерживается в контекстных соединениях.  
  
-   **SqlNotificationRequest** нельзя использовать с командами, применяемыми в контекстном соединении.  
  
-   Отмена команд, применяемых в контекстном соединении, не поддерживается. Метод **SqlCommand.Cancel** не учитывает запрос, не сообщая об этом.  
  
-   Никакие другие ключевые слова строки соединения не могут использоваться при использовании «context connection=true».  
  
-   Класс **SqlConnectionравна «context connection=true».DataSource** возвращает вместо имени экземпляра **SqlConnection** значение NULL, если строка соединения для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]равна «context connection=true».  
  
-   Установка свойства **SqlCommand.CommandTimeout** не имеет значения, если команда выполняется в контекстном соединении.  
  
## <a name="restrictions-on-regular-connections"></a>Ограничения обычных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к обычным соединениям.  
  
-   Асинхронное применение команд к внутренним серверам не поддерживается. Если в строке соединения содержится «async=true», по при последующем выполнении команды возникает исключение **System.NotSupportedException** . Отображается сообщение: «Асинхронная обработка не поддерживается при выполнении в процессе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   Объект**SqlDependency** не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
