---
title: Выполнение команды | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d9c0f935bf4d3cd903346281080a8b08384c1e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188222"
---
# <a name="executing-a-command"></a>Выполнение команды
  После установления соединения с источником данных потребитель вызывает метод **IDBCreateSession::CreateSession** метод для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс `IOpenRowset`. Метод `IOpenRowset::OpenRowset` открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors), потребитель запрашивает `IDBCreateCommand` интерфейса. Потребитель может вызвать метод `IDBCreateCommand::CreateCommand`, чтобы создать командный объект и запросить интерфейс `ICommandText`. Метод `ICommandText::SetCommandText` используется для задания текста команды, которую надо выполнить.  
  
 Для выполнения команды используется команда `Execute`. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также  
 [Создание приложения поставщика OLE DB для SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  