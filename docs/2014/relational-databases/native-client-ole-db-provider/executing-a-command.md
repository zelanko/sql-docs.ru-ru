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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f94cc014a04c3392fefb61f4fa291a8f5a44ad8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62638459"
---
# <a name="executing-a-command"></a>Выполнение команды
  После установления соединения с источником данных потребитель вызывает метод **IDBCreateSession::CreateSession** метод для создания сеанса. Сеанс выступает в роли фабрики для команд, наборов строк и транзакций.  
  
 Для непосредственной работы с отдельными таблицами и индексами потребитель запрашивает интерфейс `IOpenRowset`. Метод `IOpenRowset::OpenRowset` открывает и возвращает набор строк, содержащий все строки из единой базовой таблицы или индекса.  
  
 Для выполнения команды (например, SELECT \* FROM Authors), потребитель запрашивает `IDBCreateCommand` интерфейс. Потребитель может вызвать метод `IDBCreateCommand::CreateCommand`, чтобы создать командный объект и запросить интерфейс `ICommandText`. Метод `ICommandText::SetCommandText` используется для задания текста команды, которую надо выполнить.  
  
 Для выполнения команды используется команда `Execute`. Командой может быть любая инструкция SQL или имя процедуры. Не все команды возвращают объект результирующего набора (набор строк). Такие команды, как SELECT * FROM Authors, возвращают результирующий набор.  
  
## <a name="see-also"></a>См. также  
 [Создание приложения поставщика OLE DB для SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
