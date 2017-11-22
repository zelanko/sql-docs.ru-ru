---
title: "Параметры восстановления | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 23b028bc2e8819d63fafe0a8f915238492088fc4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="restore-options"></a>Параметры восстановления
  Существует множество способов восстановить базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , каждый из которых требует наличия разрешений администратора как на серверном компьютере, так и в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно открыть диалоговое окно **Восстановление базы данных** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выбрать необходимую конфигурацию параметров, а затем запустить операцию восстановления в диалоговом окне. Или можно создать скрипт, используя уже заданные в файле настройки. Скрипт может быть сохранен. Он будет запускаться по мере необходимости. Таким образом, операция восстановления выполняется с использованием XML для аналитики (см. описание в разделе ниже).  
  
## <a name="restoring-databases-using-xmla"></a>Восстановление баз данных с использованием XML для аналитики  
 Команда XMLA Restore представляет собой способ автоматизации процесса восстановления путем запуска операции восстановления, основанной на ABF-файле. У команды Restore есть ряд свойств, которые можно настроить так, чтобы задать определения безопасности, указать место хранения удаленных секций, а также параметры перемещения реляционных объектов OLAP (ROLAP). Дополнительные сведения см. в статье [Элемент Restore (XMLA)](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Восстановление базы данных" (службы Analysis Services — многомерные данные)](http://msdn.microsoft.com/library/a3990d47-55e2-424e-8eac-87edc937e806)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Восстановить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
