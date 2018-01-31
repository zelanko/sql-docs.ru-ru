---
title: "Возврат результатов из задачи \"Скрипт\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba7ae013e150045ba9782bba71a1be8cca4f7bee
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="returning-results-from-the-script-task"></a>Возврат результатов из задачи «Скрипт»
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
