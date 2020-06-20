---
title: Выполнение команды | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e8da036d5a4b6469a31213247ad7d4edb7dbfe
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056008"
---
# <a name="executing-a-command"></a>Выполнение команды
  После подключения с источнику данных потребитель вызывает метод **IDBCreateSession::CreateSession** для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс `IOpenRowset`. Метод `IOpenRowset::OpenRowset` открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Чтобы выполнить команду (например \* , SELECT FROM Authors), потребитель запрашивает `IDBCreateCommand` интерфейс. Потребитель может вызвать метод `IDBCreateCommand::CreateCommand`, чтобы создать командный объект и запросить интерфейс `ICommandText`. Метод `ICommandText::SetCommandText` используется для задания текста команды, которую надо выполнить.  
  
 Для выполнения команды используется команда `Execute`. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложения поставщика OLE DB для собственного клиента SQL Server](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
