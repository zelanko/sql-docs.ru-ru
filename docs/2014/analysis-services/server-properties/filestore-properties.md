---
title: Свойства хранилища файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe11b7a9cda6b3e75cb97faa17a381e2b0ea1afe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66069089"
---
# <a name="filestore-properties"></a>свойства хранилища файлов
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера хранилища файлов, перечисленные в следующих таблицах. Эти дополнительные свойства следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Многомерный и Табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 `MemoryLimit`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryLimitMin`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PercentScanPerPrice`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PerformanceTrace`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RandomFileAccessMode`  
 Логическое свойство, которое указывает, происходит ли доступ к файлам базы данных и кэшированным файлам в режиме случайного доступа к файлам. По умолчанию это свойство отлючено. По умолчанию службы Analysis Services не установливают флаг случайного доступа к файлам, когда открывают файлы данных для чтения.  
  
 Случайный доступ к файлам может быть полезен в мощных системах, особенно в системах с большими объемами памяти и несколькими узлами NUMA. В режиме случайного доступа операционная система Windows обходит операции сопоставления страниц, которые считывают данные с диска в кэш файлов системы, снижая таким образом конфликты в кэше.  
  
 Следует выполнить сравнительные проверки для определения того, можно ли повысить производительность выполнения запросов в результате изменения этого свойства. Рекомендации по выполнению сравнительных проверок (включая способы очистки кэша и предотвращения распространенных ошибок) см. в [руководстве по использованию служб SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539). Дополнительные сведения о компромиссах использования этого свойства см. в разделе [ https://support.microsoft.com/kb/2549369 ](https://support.microsoft.com/kb/2549369).  
  
 Чтобы просмотреть или изменить это свойство в среде Management Studio, необходимо включить список дополнительных свойств на странице свойств сервера. Изменить свойство можно также в файле msmdsrv.ini. После установки этого свойства рекомендуется перезапустить сервер; иначе доступ к уже открытым файлам будет продолжаться в прежнем режиме.  
  
 `UnbufferedThreshold`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="memory-model-category"></a>Категория модели памяти  
 `MemoryModel\Tax`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\Income`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\MaximumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\MinimumBalance`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\InitialBonus`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
