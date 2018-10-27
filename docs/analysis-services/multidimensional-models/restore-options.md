---
title: Параметры восстановления | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d356a642e169e252031d0e5587d37055884d66e6
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145109"
---
# <a name="restore-options"></a>Параметры восстановления
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Существует множество способов восстановить базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , каждый из которых требует наличия разрешений администратора как на серверном компьютере, так и в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно открыть диалоговое окно **Восстановление базы данных** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выбрать необходимую конфигурацию параметров, а затем запустить операцию восстановления в диалоговом окне. Или можно создать скрипт, используя уже заданные в файле настройки. Скрипт может быть сохранен. Он будет запускаться по мере необходимости. Таким образом, операция восстановления выполняется с использованием XML для аналитики (см. описание в разделе ниже).  
  
## <a name="restoring-databases-using-xmla"></a>Восстановление баз данных с использованием XML для аналитики  
 Команда XMLA Restore представляет собой способ автоматизации процесса восстановления путем запуска операции восстановления, основанной на ABF-файле. У команды Restore есть ряд свойств, которые можно настроить так, чтобы задать определения безопасности, указать место хранения удаленных секций, а также параметры перемещения реляционных объектов OLAP (ROLAP). Дополнительные сведения см. в статье [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Восстановление базы данных" (службы Analysis Services — многомерные данные)](http://msdn.microsoft.com/library/a3990d47-55e2-424e-8eac-87edc937e806)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Элемент Restore (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
