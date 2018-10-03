---
title: Параметры восстановления | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 348e3254cb31cfef72e40b35ac74cbe9cf578834
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060374"
---
# <a name="restore-options"></a>Параметры восстановления
  Существует множество способов восстановить базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , каждый из которых требует наличия разрешений администратора как на серверном компьютере, так и в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно открыть диалоговое окно **Восстановление базы данных** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выбрать необходимую конфигурацию параметров, а затем запустить операцию восстановления в диалоговом окне. Или можно создать скрипт, используя уже заданные в файле настройки. Скрипт может быть сохранен. Он будет запускаться по мере необходимости. Таким образом, операция восстановления выполняется с использованием XML для аналитики (см. описание в разделе ниже).  
  
## <a name="restoring-databases-using-xmla"></a>Восстановление баз данных с использованием XML для аналитики  
 Команда XMLA Restore представляет собой способ автоматизации процесса восстановления путем запуска операции восстановления, основанной на ABF-файле. У команды Restore есть ряд свойств, которые можно настроить так, чтобы задать определения безопасности, указать место хранения удаленных секций, а также параметры перемещения реляционных объектов OLAP (ROLAP). Дополнительные сведения см. в статье [Restore Element &#40;XMLA&#41;](../xmla/xml-elements-commands/restore-element-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
## <a name="see-also"></a>См. также  
 [Восстановление базы данных-диалоговое окно &#40;службы Analysis Services — многомерные данные&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](backup-and-restore-of-analysis-services-databases.md)   
 [Элемент RESTORE &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/restore-element-xmla.md)   
 [Резервное копирование, восстановление и синхронизация баз данных &#40;XML для Аналитики&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
