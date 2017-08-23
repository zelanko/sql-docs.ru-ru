---
title: "Ведение журнала в компоненте скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 410a2472399574753d67a44b93437b1698c8b086
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-component"></a>Ведение журнала в компоненте скрипта
  Ведение журнала в пакетах служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] позволяет сохранить подробные сведения о процессе выполнения, результатах и проблемах, записывая стандартные события или определенные пользователем сообщения с целью последующего анализа. Можно использовать компонент скрипта <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> метод **ScriptMain** класс пользовательские данные журнала. Если включено ведение журнала и **ScriptComponentLogEntry** событие выбирается для регистрации **сведения** вкладке **Настройка журналов служб SSIS** диалоговое окно, в рамках одного вызова <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> метод сохраняет сведения о событии в все регистраторы, настроенные для задачи потока данных.  
  
 Далее приведен простой пример ведения журнала.  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Хотя журнал можно вести непосредственно из компонента скрипта, может потребоваться реализовать события, а не журнал. При использовании событий кто угодно может включить запись сообщений о событиях в журнал, но можно использовать для отклика на события стандартные или определяемые пользователем обработчики событий.  
  
 Дополнительные сведения о ведении журнала см. в разделе [службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
