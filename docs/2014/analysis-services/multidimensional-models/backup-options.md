---
title: Создать резервную копию параметров | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce7ca784325be140ffbd62880be2fb717ce058f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257290"
---
# <a name="backup-options"></a>Параметры резервного копирования
  Существует несколько способов резервного копирования баз данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и все они требуют прав администратора сервера и базы данных. Можно открыть диалоговое окно **Резервное копирование** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], установить нужную конфигурацию параметров, а затем запустить резервное копирование из самого окна. Кроме этого, можно создать скрипт, используя настройки, уже заданные в файле. Затем скрипт можно сохранить и запускать так часто, как требуется.  
  
## <a name="backup-and-synchronize"></a>Резервное копирование и синхронизация  
 Если база данных расположена на удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], можно использовать функцию синхронизации для резервного копирование базы данных на локальный экземпляр. Таким образом можно переносить сборки базы данных из среды разработки в производственную среду. Также можно использовать обычные операции резервного копирования и восстановления на уровне файлов, чтобы переместить сборку из среды разработки в производственную среду, но синхронизация предоставляет дополнительные возможности. Например, параметры безопасности могут различаться на компьютере для разработки и производственном компьютере. Синхронизация предоставит возможность сохранить эти настройки и синхронизировать все объекты, кроме ролей. Кроме того, синхронизация обычно производит добавочные обновления тех объектов, которые различаются на компьютерах источника и назначения. Такой тип добавочного резервного копирования не доступен для функции резервного копирования и восстановления. Дополнительные сведения см. в разделе [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  У учетной записи служб Analysis Services должны быть разрешения на запись в папку резервного копирования, заданную для каждого из файлов. Кроме того, пользователь должен быть членом одной из следующих ролей: роли администратора в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роли базы данных с разрешениями «Полный доступ (Администратор)» в базе данных, для которой создается резервная копия.  
  
## <a name="see-also"></a>См. также  
 [Создать резервную копию базы данных-диалоговое окно &#40;службы Analysis Services — многомерные данные&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](backup-and-restore-of-analysis-services-databases.md)   
 [Резервное копирование элемента &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/backup-element-xmla.md)   
 [Резервное копирование, восстановление и синхронизация баз данных &#40;XML для Аналитики&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
