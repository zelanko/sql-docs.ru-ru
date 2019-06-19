---
title: Возврат результатов из задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 59a9ce64016cb4a3b748b504895262bce6be58d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65724053"
---
# <a name="returning-results-from-the-script-task"></a>Возврат результатов из задачи «Скрипт»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Задача «Скрипт» использует свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> и дополнительное свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> для возвращения сведений о состоянии в среду выполнения служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], которые могут быть использованы для определения пути рабочего процесса по завершении задачи «Скрипт».  
  
## <a name="taskresult"></a>TaskResult  
 Свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> сообщает о том, успешным или неуспешным было выполнение задачи. Пример:  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 При необходимости свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> возвращает определяемый пользователем объект, который содержит количественные или иные дополнительные сведения об успешном или неуспешном выполнении задачи «Скрипт». Например, задача «FTP» использует свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> для возврата числа переданных файлов. Задача «Выполнение SQL» возвращает число строк, затронутых при выполнении задачи. Свойство <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> может также использоваться для определения пути рабочего процесса. Пример:  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
