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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ef641bbfb94b8fde5f12af6cadd03f13fbfa91f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761170"
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
