---
title: Подключение к источникам данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 99ced09e841e4a778b9920ced4023336a1668d2d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701142"
---
# <a name="connecting-to-data-sources"></a>Подключение к источникам данных
ADO **подключения** представляет уникальный сеанс с источником данных, включая СУБД, хранилище файлов или файлов с разделителями-запятыми. В случае клиент/сервер СУБД соединение ADO может быть действительное сетевое подключение к серверу.  
  
 **Подключения** объект поддерживает различные [свойства и методы](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) для указания конфигурации подключений, открытие и закрытие подключений, создания и выполнения команд в источнике данных и предоставляем сведения о структуре источника данных в виде наборов строк схемы, и т.д. В зависимости от функциональных возможностей, поддерживаемых поставщиком, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.  
  
 Можно подключиться к источнику данных с помощью **подключения** объекта или с помощью **записей** объекта.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование объекта Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Использование объекта Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Указание свойств подключения](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Управление транзакциями](../../../ado/guide/data/controlling-transactions-ado.md)
