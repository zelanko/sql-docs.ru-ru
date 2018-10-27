---
title: Создать резервную копию параметров | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62f5bf26f80ea1018a5a3330efa0f055021ff0f5
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145445"
---
# <a name="backup-options"></a>Параметры резервного копирования
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Существует несколько способов резервного копирования баз данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и все они требуют прав администратора сервера и базы данных. Можно открыть диалоговое окно **Резервное копирование** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], установить нужную конфигурацию параметров, а затем запустить резервное копирование из самого окна. Кроме этого, можно создать скрипт, используя настройки, уже заданные в файле. Затем скрипт можно сохранить и запускать так часто, как требуется.  
  
## <a name="backup-and-synchronize"></a>Резервное копирование и синхронизация  
 Если база данных расположена на удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], можно использовать функцию синхронизации для резервного копирование базы данных на локальный экземпляр. Таким образом можно переносить сборки базы данных из среды разработки в производственную среду. Также можно использовать обычные операции резервного копирования и восстановления на уровне файлов, чтобы переместить сборку из среды разработки в производственную среду, но синхронизация предоставляет дополнительные возможности. Например, параметры безопасности могут различаться на компьютере для разработки и производственном компьютере. Синхронизация предоставит возможность сохранить эти настройки и синхронизировать все объекты, кроме ролей. Кроме того, синхронизация обычно производит добавочные обновления тех объектов, которые различаются на компьютерах источника и назначения. Такой тип добавочного резервного копирования не доступен для функции резервного копирования и восстановления. Дополнительные сведения см. в разделе [Synchronize Analysis Services Databases](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  У учетной записи служб Analysis Services должны быть разрешения на запись в папку резервного копирования, заданную для каждого из файлов. Кроме того, пользователь должен быть членом одной из следующих ролей: роли администратора в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роли базы данных с разрешениями «Полный доступ (Администратор)» в базе данных, для которой создается резервная копия.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Создание резервной копии базы данных" (службы Analysis Services — многомерные данные)](http://msdn.microsoft.com/library/7811ce7d-6c37-4189-bfa6-ef36fb4932db)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Элемент Backup (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
