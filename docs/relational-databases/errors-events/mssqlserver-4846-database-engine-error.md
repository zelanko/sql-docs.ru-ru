---
title: "MSSQLSERVER_4846 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0b9152072fde4c139602eecef4a182e3e2cd1300
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver4846"></a>MSSQLSERVER_4846
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|4846|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|BULKPROV_MEMORY|  
|Текст сообщения|Поставщику массовых данных не удалось выделить память.|  
  
## <a name="explanation"></a>Объяснение  
Ошибка выделения памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Для диагностики ошибок памяти выполните следующие шаги.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для **SQL Server: диспетчер буферов**, **SQL Server: диспетчер памяти**.  
  
3.  Проверьте следующие параметры конфигурации памяти SQL Server.  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Обращайте внимание на любые необычные настройки. При необходимости измените их. Учтите требования [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] к объему памяти. Параметры по умолчанию приведены в разделе «Настройка параметров конфигурации сервера» электронной документации по SQL Server.  
  
4.  Обратите внимание на сообщения инструкции DBCC MEMORYSTATUS и способ их изменения при появлении сообщений об ошибках.  
  
5.  Проверьте рабочую нагрузку (например, число параллельных сеансов, в текущий момент выполняющих запросы).  
  
Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если какие-либо отличные от SQL Server приложения используют необходимые ресурсы, попытайтесь прекратить выполнение этих приложений или перенесите их выполнение на отдельный сервер. Это снизит внешнюю нагрузку на память.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  

