---
description: Подключение к источникам данных
title: Подключение к источникам данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 988eef3a3eb706480e50f0feb6d2fe363b4faabd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991525"
---
# <a name="connecting-to-data-sources"></a>Подключение к источникам данных
Объект **соединения** ADO представляет собой уникальный сеанс с источником данных, включая СУБД, хранилище файлов или текстовый файл с разделителями-запятыми. В случае с системой базы данных клиента или сервера соединение ADO может быть реальным сетевым подключением к серверу.  
  
 Объект **Connection** поддерживает различные [Свойства и методы](../../reference/ado-api/connection-object-properties-methods-and-events.md) для указания конфигураций соединения, открытия и закрытия соединений, создания и выполнения команд для источника данных, а также предоставления сведений о структуре базового источника данных в форме наборов строк схемы и т. д. В зависимости от функциональности, поддерживаемой поставщиком, некоторые коллекции, методы или свойства объекта **соединения** могут быть недоступны.  
  
 Подключиться к источнику данных можно либо с помощью объекта **соединения** , либо с помощью объекта **Recordset** .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование объекта Connection](./using-a-connection-object.md)  
  
-   [Использование объекта Recordset](./using-a-recordset-object.md)  
  
-   [Создание строки подключения](./creating-a-connection-string.md)  
  
-   [Указание свойств подключения](./specifying-connection-properties.md)  
  
-   [Управление транзакциями](./controlling-transactions-ado.md)