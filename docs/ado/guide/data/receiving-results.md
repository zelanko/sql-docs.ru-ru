---
title: Получение результатов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b861553e9a71ce56377f8d87bba0f9e26e929c2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924526"
---
# <a name="receiving-results"></a>Получение результатов
В ADO большинство команд приводят к получению некоторой информации вызывающему объекту. Для команд, возвращающих набор строк, результаты получаются в объекте **набора записей** , который, вероятно, наиболее часто используется объектами ADO.  
  
 Существует несколько способов получения данных в объекте **набора записей** из источника данных, включая вызов следующего:  
  
-   [Метод Connection. Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Command. Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Recordset. Open](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection. Намедкомманд](../../../ado/guide/data/named-commands.md)  
  
-   [Connection. StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Получение данных в объекте **набора записей** завершает процесс получения данных с участием объекта **соединения** и объекта **команды** , неявно или явно. В типичной системе клиентских и серверных приложений весь процесс получения данных требует цикла обработки по сети для каждого заполненного **набора записей**.  
  
 Чтобы получить более одного результирующего набора, необходимо выполнить несколько циклов обработки по сети, по одному для каждого набора данных, инкапсулированного в объекте **набора записей** . При использовании высокодоступных или перегруженных сетей уменьшение числа круговых путей может помочь улучшить производительность приложения. Поэтому некоторые поставщики предлагают поддержку для получения нескольких **наборов записей**в одном цикле обработки. Это рассматривается в следующем разделе:  
  
-   [Получение нескольких наборов записей](../../../ado/guide/data/receiving-multiple-recordsets.md)
