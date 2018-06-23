---
title: Настройка — каталоги данных служб Analysis Services | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
caps.latest.revision: 20
author: HeidiSteen
ms.author: heidist
manager: jhubbard
ms.openlocfilehash: b3b945938c0ffd8a5059f8b2c53546538ea97eee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190378"
---
# <a name="analysis-services-configuration---data-directories"></a>Настройка служб Analysis Services — каталоги данных
  Приведенные в следующей таблице каталоги по умолчанию можно изменить с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Разрешение на доступ к этим файлам предоставляется локальным администраторам и членам группы безопасности SQLServerMSASUser$\<экземпляр>, которая создается и настраивается во время установки.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
  
|Описание|Каталог по умолчанию|Рекомендации|  
|-----------------|-----------------------|---------------------|  
|Корневой каталог данных|C:\Program Files\Microsoft SQL Server\MSAS12. \<Идентификатор экземпляра > \OLAP\Data\|убедитесь, что папка SQL Server\ \Program files\Microsoft защищена ограниченными разрешениями. Во многих конфигурациях производительность служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] зависит от производительности хранилища, в котором размещается каталог данных. Поместите этот каталог в доступном хранилище, имеющем самое высокое быстродействие. При установке отказоустойчивых кластеров каталоги данных должны находиться на общем диске.|  
|Каталог файла журнала|C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID > \OLAP\Log\|это каталог для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] файлы журнала, она содержит журнал FlightRecorder. При увеличении времени существования «черного ящика» позаботьтесь о том, чтобы в каталоге журнала было достаточно места.|  
|Каталог temp|C:\Program Files\Microsoft SQL Server\MSAS12. \<Идентификатор экземпляра > \OLAP\Temp\|поместите каталог Temp в высокопроизводительном хранилище.|  
|Каталог резервного копирования|C:\Program Files\Microsoft SQL Server\MSAS12. \<Идентификатор экземпляра > \OLAP\Backup\|это каталог для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] файлов резервных копий по умолчанию. Здесь же системная служба PowerPivot кэширует файлы данных PowerPivot для установок SharePoint.<br /><br /> Убедитесь, что заданы соответствующие разрешения, чтобы предотвратить потерю данных, а также что группа пользователей для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеет достаточные разрешения для записи в каталог резервных копий. Использование подключенных дисков для размещения каталогов резервного копирования не поддерживается.|  
  
## <a name="notes"></a>Примечания  
  
-   Экземпляры служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], развернутые в ферме SharePoint, хранят файлы приложений, файлы данных и свойства в базах данных содержимого и базах данных приложений служб.  
  
-   При добавлении компонентов в существующую конфигурацию невозможно ни изменить расположение ранее установленного компонента, ни указать расположение нового.  
  
-   Если при установке были указаны каталоги, отличные от каталогов по умолчанию, проверьте их уникальность для данного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ни один из каталогов, заданных в этом диалоговом окне, не должен совпадать с каталогами, указанными для других экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] и службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] должны быть установлены на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разные каталоги.  
  
-   Программные файлы и файлы данных невозможно установить:  
  
    -   на съемный диск  
  
    -   в файловую систему, использующую сжатие  
  
    -   в каталог, в котором находятся системные файлы  
  
## <a name="see-also"></a>См. также  
 [Расположение файлов для экземпляра по умолчанию и именованных экземпляров SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  