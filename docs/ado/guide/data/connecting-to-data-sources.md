---
description: Подключение к источникам данных
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 78d7395adfb30dbf78d88baadabc42ede409f47a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453646"
---
# <a name="connecting-to-data-sources"></a>Подключение к источникам данных
Объект **соединения** ADO представляет собой уникальный сеанс с источником данных, включая СУБД, хранилище файлов или текстовый файл с разделителями-запятыми. В случае с системой базы данных клиента или сервера соединение ADO может быть реальным сетевым подключением к серверу.  
  
 Объект **Connection** поддерживает различные [Свойства и методы](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) для указания конфигураций соединения, открытия и закрытия соединений, создания и выполнения команд для источника данных, а также предоставления сведений о структуре базового источника данных в форме наборов строк схемы и т. д. В зависимости от функциональности, поддерживаемой поставщиком, некоторые коллекции, методы или свойства объекта **соединения** могут быть недоступны.  
  
 Подключиться к источнику данных можно либо с помощью объекта **соединения** , либо с помощью объекта **Recordset** .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование объекта Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Использование объекта Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Создание строки подключения](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Указание свойств подключения](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Управление транзакциями](../../../ado/guide/data/controlling-transactions-ado.md)
