---
title: "Параметры резервного копирования | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "резервное копирование баз данных [службы Analysis Services]"
  - "базы данных [службы Analysis Services], резервное копирование"
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Параметры резервного копирования
  Существует несколько способов резервного копирования баз данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], и все они требуют прав администратора сервера и базы данных. Можно открыть диалоговое окно **Резервное копирование** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], установить нужную конфигурацию параметров, а затем запустить резервное копирование из самого окна. Кроме этого, можно создать скрипт, используя настройки, уже заданные в файле. Затем скрипт можно сохранить и запускать так часто, как требуется.  
  
## Резервное копирование и синхронизация  
 Если база данных расположена на удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], можно использовать функцию синхронизации для резервного копирование базы данных на локальный экземпляр. Таким образом можно переносить сборки базы данных из среды разработки в производственную среду. Также можно использовать обычные операции резервного копирования и восстановления на уровне файлов, чтобы переместить сборку из среды разработки в производственную среду, но синхронизация предоставляет дополнительные возможности. Например, параметры безопасности могут различаться на компьютере для разработки и производственном компьютере. Синхронизация предоставит возможность сохранить эти настройки и синхронизировать все объекты, кроме ролей. Кроме того, синхронизация обычно производит добавочные обновления тех объектов, которые различаются на компьютерах источника и назначения. Такой тип добавочного резервного копирования не доступен для функции резервного копирования и восстановления. Дополнительные сведения см. в разделе [Synchronize Analysis Services Databases](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  У учетной записи служб Analysis Services должны быть разрешения на запись в папку резервного копирования, заданную для каждого из файлов. Кроме того, пользователь должен быть членом одной из следующих ролей: роли администратора в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или роли базы данных с разрешениями «Полный доступ (Администратор)» в базе данных, для которой создается резервная копия.  
  
## См. также раздел  
 [Диалоговое окно "Создание резервной копии базы данных" (службы Analysis Services — многомерные данные)](../Topic/Backup%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Элемент Backup (XMLA)](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Резервное копирование, восстановление и синхронизация баз данных (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  