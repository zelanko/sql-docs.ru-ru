---
title: MSSQLSERVER_802 | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: bd0ed39287cd9f4a61888aba817821f0ef16e584
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193792"
---
# <a name="mssqlserver802"></a>MSSQLSERVER_802
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|802|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NO_BUFS|  
|Текст сообщения|Недостаточно свободной памяти в буферном пуле.|  
  
## <a name="explanation"></a>Объяснение  
 Это происходит, если буферный пул заполнен и не может больше увеличиваться.  
  
## <a name="user-action"></a>Действие пользователя  
 Далее представлены общие шаги, которые помогут при устранении неполадок с памятью.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: диспетчер буферов**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: диспетчер памяти**.  
  
3.  Проверьте следующие параметры конфигурации памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
     Обратите внимание на любые необычные параметры и исправьте их при необходимости. Принимайте во внимание тот факт, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предъявляются повышенные требования к доступному объему памяти. Настройки по умолчанию приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разделе «Настройка параметров конфигурации сервера».  
  
4.  Обратите внимание на сообщения инструкции DBCC MEMORYSTATUS и способ их изменения при появлении сообщений об ошибках.  
  
5.  Проверьте рабочую нагрузку (число параллельных сеансов, выполняющихся запросов).  
  
 Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если ресурсы потребляют приложения, выполняющиеся вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], попробуйте остановить эти приложения или выполнить их на отдельном сервере.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
 Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  
  