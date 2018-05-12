---
title: Изменение или удаление базы данных служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44952f477cf16a169ad96f2bfe881b16ee9738da
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="modify-or-delete-an-analysis-services-database"></a>Изменение или удаление базы данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Имя и описание базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перед развертыванием можно изменить в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , а после развертывания — в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Можно также изменять дополнительные настройки в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в зависимости от среды.  
  
> [!NOTE]  
>  Нельзя изменять свойства базы данных, используя среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети.  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>Изменение баз данных с помощью среды SQL Server Management Studio  
 После развертывания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы изменить режим олицетворения, используемый службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при подключении к источникам данных, содержащимся в этой базе данных. Режим олицетворения позволяет задать контекст безопасности, используемый службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при попытке подключения к источнику данных для обработки, просмотра или детализации.  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>Изменение баз данных с помощью средств SQL Server Data Tools  
 Можно использовать среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта, чтобы изменить переводы для заголовка и описания проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , используемого для определения базы данных. Дополнительные сведения об использовании переводов в базе данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Сценарии глобализации для служб Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md).  
  
 Можно также установить псевдонимы и статистические функции, связанные с типами счетов, используемыми атрибутами счетов в измерениях, содержащихся в базе данных. Псевдонимы позволяют выбрать специфическую терминологию, используемую в организации для типов счетов в плане счетов. Типы счетов используются элементами атрибута счетов для указания способов статистической обработки мер по каждому элементу с использованием статистических функций, указанных для каждого типа счета, содержащегося в базе данных. Дополнительные сведения об атрибутах учетной записи см. в статье [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="deleting-databases"></a>удаление баз данных  
 При удалении существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляются база данных и все кубы, измерения и модели интеллектуального анализа данных, содержащиеся в этой базе данных. Удалить существующую базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно только в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-delete-an-analysis-services-database"></a>Удаление базы данных служб Analysis Services  
  
1.  Подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  В окне **Обозреватель объектов**разверните узел для подключенного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и убедитесь, что объект, который требуется удалить, видимый.  
  
3.  Щелкните правой кнопкой мыши объект, который требуется удалить, и выберите **Удалить**.  
  
4.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Document and Script базы данных служб Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
  
