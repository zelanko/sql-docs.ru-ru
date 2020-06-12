---
title: Конфигурация Analysis Services — каталоги данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 47d4299cde4575f7443faa1546aeffdb41fe12d5
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/26/2020
ms.locfileid: "83859176"
---
# <a name="analysis-services-configuration---data-directories"></a>Настройка служб Analysis Services — каталоги данных
  Приведенные в следующей таблице каталоги по умолчанию можно изменить с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Разрешение на доступ к этим файлам предоставляется локальным администраторам и членам группы безопасности SQLServerMSASUser$\<экземпляр>, которая создается и настраивается во время установки.  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
  
|Описание|Каталог по умолчанию|Рекомендации|  
|-----------------|-----------------------|---------------------|  
|Корневой каталог данных|C:\Program Files\Microsoft SQL Server\MSAS12. \< InstanceID> \OLAP\Data \| Убедитесь, что папка \Program files\Microsoft SQL Server \ защищена с ограниченными разрешениями. Во многих конфигурациях производительность служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] зависит от производительности хранилища, в котором размещается каталог данных. Поместите этот каталог в доступном хранилище, имеющем самое высокое быстродействие. При установке отказоустойчивых кластеров каталоги данных должны находиться на общем диске.|  
|Каталог файла журнала|C:\Program Files\Microsoft SQL Server\MSAS12. \< InstanceID> \Olap\log. \| . это каталог для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] файлов журнала, который включает журнал FlightRecorder. При увеличении времени существования «черного ящика» позаботьтесь о том, чтобы в каталоге журнала было достаточно места.|  
|Каталог temp|C:\Program Files\Microsoft SQL Server\MSAS12. \< InstanceID> \Олап\темп \| помещает временный каталог в подсистему хранения данных высокой производительности.|  
|Каталог резервного копирования|C:\Program Files\Microsoft SQL Server\MSAS12. \< InstanceID> \Олап\баккуп \| . это каталог для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] файлов резервных копий по умолчанию. Здесь же системная служба PowerPivot кэширует файлы данных PowerPivot для установок SharePoint.<br /><br /> Убедитесь, что заданы соответствующие разрешения, чтобы предотвратить потерю данных, а также что группа пользователей для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеет достаточные разрешения для записи в каталог резервных копий. Использование подключенных дисков для размещения каталогов резервного копирования не поддерживается.|  
  
## <a name="notes"></a>Примечания  
  
-   Экземпляры служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], развернутые в ферме SharePoint, хранят файлы приложений, файлы данных и свойства в базах данных содержимого и базах данных приложений служб.  
  
-   При добавлении компонентов в существующую конфигурацию невозможно ни изменить расположение ранее установленного компонента, ни указать расположение нового.  
  
-   Если при установке были указаны каталоги, отличные от каталогов по умолчанию, проверьте их уникальность для данного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ни один из каталогов, заданных в этом диалоговом окне, не должен совпадать с каталогами, указанными для других экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] и службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] должны быть установлены на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разные каталоги.  
  
-   Программные файлы и файлы данных невозможно установить:  
  
    -   на съемный диск  
  
    -   в файловую систему, использующую сжатие  
  
    -   в каталог, в котором находятся системные файлы  
  
## <a name="see-also"></a>См. также:  
 [Расположение файлов для экземпляра по умолчанию и именованных экземпляров SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
