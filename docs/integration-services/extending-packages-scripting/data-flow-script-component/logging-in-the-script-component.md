---
title: Ведение журнала в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 44bb7079f01fbf745b514a8930be734477f21359
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913412"
---
# <a name="logging-in-the-script-component"></a>Ведение журнала в компоненте скрипта

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Ведение журнала в пакетах служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] позволяет сохранить подробные сведения о процессе выполнения, результатах и проблемах, записывая стандартные события или определенные пользователем сообщения с целью последующего анализа. Компонент скрипта может использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> класса **ScriptMain** для записи определяемых пользователем данных. Если ведение журнала включено и событие **ScriptComponentLogEntry** выбрано для записи на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS**, единичный вызов метода <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> сохраняет сведения о событии во всех поставщиках журналов, настроенных для задачи потока данных.  
  
 Далее приведен простой пример ведения журнала.  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Хотя журнал можно вести непосредственно из компонента скрипта, может потребоваться реализовать события, а не журнал. При использовании событий кто угодно может включить запись сообщений о событиях в журнал, но можно использовать для отклика на события стандартные или определяемые пользователем обработчики событий.  
  
 Дополнительные сведения о ведении журналов см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>См. также:  
 [Ведение журналов в службах Integration Services (SSIS)](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
