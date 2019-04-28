---
title: Изменение или удаление базы данных служб Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bcb8d635721a31429f387d135ed7b0bbf7112d6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725318"
---
# <a name="modify-or-delete-an-analysis-services-database"></a>Изменение или удаление базы данных служб Analysis Services
  Имя и описание базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перед развертыванием можно изменить в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , а после развертывания — в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Можно также изменять дополнительные настройки в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в зависимости от среды.  
  
> [!NOTE]  
>  Нельзя изменять свойства базы данных, используя среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети.  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>Изменение баз данных с помощью среды SQL Server Management Studio  
 После развертывания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы изменить режим олицетворения, используемый службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при подключении к источникам данных, содержащимся в этой базе данных. Режим олицетворения позволяет задать контекст безопасности, используемый службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при попытке подключения к источнику данных для обработки, просмотра или детализации.  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>Изменение баз данных с помощью средств SQL Server Data Tools  
 Можно использовать среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта, чтобы изменить переводы для заголовка и описания проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , используемого для определения базы данных. Дополнительные сведения об использовании переводов в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных, см. в разделе [сценарии глобализации для многомерных служб Analysis Services](../globalization-scenarios-for-analysis-services-multiidimensional.md).  
  
 Можно также установить псевдонимы и статистические функции, связанные с типами счетов, используемыми атрибутами счетов в измерениях, содержащихся в базе данных. Псевдонимы позволяют выбрать специфическую терминологию, используемую в организации для типов счетов в плане счетов. Типы счетов используются элементами атрибута счетов для указания способов статистической обработки мер по каждому элементу с использованием статистических функций, указанных для каждого типа счета, содержащегося в базе данных. Дополнительные сведения об атрибутах учетной записи см. в статье [Атрибуты и иерархии атрибутов](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="deleting-databases"></a>удаление баз данных  
 При удалении существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляются база данных и все кубы, измерения и модели интеллектуального анализа данных, содержащиеся в этой базе данных. Удалить существующую базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно только в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-delete-an-analysis-services-database"></a>Удаление базы данных служб Analysis Services  
  
1.  Подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  В окне **Обозреватель объектов**разверните узел для подключенного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и убедитесь, что объект, который требуется удалить, видимый.  
  
3.  Щелкните правой кнопкой мыши объект, который требуется удалить, и выберите **Удалить**.  
  
4.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Документирование и работа со скриптами в базе данных служб Analysis Services](document-and-script-an-analysis-services-database.md)  
  
  
