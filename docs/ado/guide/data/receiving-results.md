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
manager: craigg
ms.openlocfilehash: 648fd220988a0b32837ddcdf2b4c1c23de5e9f69
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657112"
---
# <a name="receiving-results"></a>Получение результатов
В ADO большинство команд привести некоторые сведения, возвращается вызывающей стороне. Для команд, возвращает набор строк, результаты получаются в **записей** объект, который является, вероятно, наиболее часто используемые объекты ADO.  
  
 Существует несколько способов для получения данных в **записей** объекта из источника данных, включая вызов следующее:  
  
-   [Метод Connection.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Command.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Recordset.Open](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Получение данных в **записей** объект завершается процесс получения данных, с участием **подключения** объекта и **команда** объекта, неявно или явным образом. В системе, приложение обычно клиент/сервер, весь процесс получения данных требуется цикл обработки по сети для каждого заполнения **записей**.  
  
 Чтобы получать несколько результирующих наборов означает, что требуется сделать несколько круговых путей по сети, одной для каждого набора данных, инкапсулированных в **записей** объекта. Для сетей медленная или перегружена уменьшение числа двусторонних передач сигнала может повысить производительность приложения. Таким образом, некоторые поставщики предлагают поддержку для получения нескольких **записей**s в рамках одного цикла обработки. Этот вопрос рассматривается в следующем разделе:  
  
-   [Получение нескольких наборов записей](../../../ado/guide/data/receiving-multiple-recordsets.md)
