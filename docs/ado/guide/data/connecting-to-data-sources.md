---
title: "Подключение к источникам данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 47aa7f058db324c7388801ae6a391b6c0c24ae1d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-to-data-sources"></a>Подключение к источникам данных
ADO **подключения** представляет уникальный сеанс с источником данных, включая СУБД, хранилище файла или файл с разделителями-запятыми. В случае система клиент сервер базы данных соединение ADO может быть действительное сетевое подключение к серверу.  
  
 **Подключения** объект поддерживает различные [свойства и методы](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) для указания конфигурации соединения, открытие и закрытие соединений, создания и выполнения команд в источнике данных и предоставляет сведения о проектировании базового источника данных в виде наборов строк схемы, и т. д. В зависимости от функциональных возможностей, поддерживаемых поставщика, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.  
  
 Можно подключиться к источнику данных с помощью **подключения** объекта или с помощью **записей** объекта.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [С помощью объекта соединения](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [С помощью объекта набора записей](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Указание свойств соединения](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Управление транзакциями](../../../ado/guide/data/controlling-transactions-ado.md)
